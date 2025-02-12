1. vi \[filename]
Seems to include number of the city, details of the city location, coordinates, country, dates, capital, and population among other details 
2. grep -i 'toronto' \[filename]
uses grep to search for patterns, 
-i makes the search case insensitive, 
toronto is the specified word i want to search, 
and file name is just the specified file
3. awk -F, '$6 == "Canada" {print $2}' daily_temperature_1000_cities_1980_2020_transformed.csv | sort -u
using awk to give an comprehensive output instead of grep 
'-F,' sets the field separator to a comma
'$6 == "Canada" {print $2}'  checks for column 6 to see if it is Canada, if so, then print out the city in column 2
sort -u removes duplicates 
4. awk -F, '$6 == "Canada"' daily_temperature_1000_cities_1980_2020_transformed.csv > canada_cities.csv
Everything is the same except now there is not {print $2} to specify to only extract cities and no other data, 
\> canada_cities.csv specifies the extraction to a csv file
5. files are linked externally
6. original file is only 325 bytes, while the preprocessed file is 943kb
![[Pasted image 20250211223835.png]] 
```c++
template<typename _Tp>
    constexpr int
    __countr_zero(_Tp __x) noexcept
    {
      using __gnu_cxx::__int_traits;
      constexpr auto _Nd = __int_traits<_Tp>::__digits;

      if (__x == 0)
        return _Nd;

      constexpr auto _Nd_ull = __int_traits<unsigned long long>::__digits;
      constexpr auto _Nd_ul = __int_traits<unsigned long>::__digits;
      constexpr auto _Nd_u = __int_traits<unsigned>::__digits;

      if constexpr (_Nd <= _Nd_u)
 return __builtin_ctz(__x);
      else if constexpr (_Nd <= _Nd_ul)
 return __builtin_ctzl(__x);
      else if constexpr (_Nd <= _Nd_ull)
 return __builtin_ctzll(__x);
      else
 {
   static_assert(_Nd <= (2 * _Nd_ull),
   "Maximum supported integer size is 128-bit");

   constexpr auto __max_ull = __int_traits<unsigned long long>::__max;
   unsigned long long __low = __x & __max_ull;
   if (__low != 0)
     return __builtin_ctzll(__low);
   unsigned long long __high = __x >> _Nd_ull;
   return __builtin_ctzll(__high) + _Nd_ull;
 }
    }
```
this is a template function, which counts the number of trailing zeros in the binary rep of an int. This is also a generic function meaning it can work with any integer type. it also is not allowed to throw any exceptions.  
7. There are no direct syscalls, however, there are call functions that eventually call the system
call	\_ZNSt14basic_ifstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode@PLT, builds on top of system calls, but itself does not constitute to be a system call.
I am also using a x86 machine which may complicate the system call procedures.