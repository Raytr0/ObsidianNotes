Unit 5 practice:
PaymentMethod(pMethodNo)
PK: pMethodNo

Customer(customerNo)
PK: customerNo

Product(productNo)
PK: productNo

ShipmentMethod(sMethodNo)
PK: sMethodNo

Invoice(invoiceNo, pMethodNo)
PK: invoiceNo
FK: pMethodNo
FK: orderNo

