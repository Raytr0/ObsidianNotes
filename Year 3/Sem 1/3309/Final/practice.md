### Exercise 1:
```SQL
SELECT *
FROM Guest
WHERE guestNo IN ( SELECT guestNo
				FROM Booking
				WHERE dateFrom <= CURRENT_DATE AND 
				dateTo >= CURRENT_DATE AND
				hotelNo = (SELECT hotelNo
								FROM Hotel
								WHERE hotelName = 'Grosvenor Hotel')
)
```
Has to use IN in third row instead of an = because this is comparing multiple guestNo values, = only compares single, if wanting to use = you need a bunch of OR statements
Date restriction because question asks for CURRENTLY staying at hotel

### Exercise 2:
```SQL
SELECT price, type
FROM Room
JOIN Hotel on Hotel.hotelNo = Room.hotelNo 
WHERE hotelName = 'Grosvenor Hotel';
```
```SQL
SELECT g.*
FROM Guest g
JOIN Booking b on b.guestNo = g.guestNo
JOIN Hotel h on h.hotelNo = b.hotelNo
WHERE h.hotelName = 'Grosvenor Hotel' AND 
		dateFrom <= CURRENT_DATE AND 
		dateTo >= CURRENT_DATE ;
```
Again remember to include date parameters, question said CURRENTLY
3. How many visits did each hotel have? Include the hotel name and the number of visits
```SQL
SELECT h.hotelName, COUNT(guestNo)
FROM Hotel h
JOIN Booking b on b.hotelNo=h.hotelNo
GROUP BY h.hotelNO, h.hotelName;
```
4. How many different guests visited each hotel? Include the hotel name and the number of different guests
```SQL
SELECT h.hotelName, COUNT(DISTINCT guestNo)
FROM Hotel h
JOIN Booking b on b.hotelNo=h.hotelNo
GROUP BY h.hotelNO, h.hotelName;
```
5. Which hotels had more than 3 visits? Include the hotel name and the number of visits
```SQL
SELECT h.hotelName, COUNT(guestNo)
FROM Hotel h
JOIN Booking b on b.hotelNo=h.hotelNo
GROUP BY h.hotelNO, h.hotelName
HAVING COUNT(guestNO)>3;
```
Need to using HAVING for aggregates and grouping

### Exercise 3:
