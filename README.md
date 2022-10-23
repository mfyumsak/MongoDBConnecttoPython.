# MongoDBConnecttoPython.
Mongo Working First
!pip3 install pymongo[srv]
from pymongo import MongoClient
client=MongoClient("mongodb+srv://mfurkanyBTK:mf1234@istanbulbtkacademy.7ogcdwd.mongodb.net/admin")
print(client.list_database_names())
dblist1=client.list_database_names()
if "23June_DB" in dblist1:
   print("Veri tabanı var")
else:
   print("Maalesef DB bulunamadı")
   dblist2=client.list_database_names()
dbByuser=input("Veritabanı adını giriniz")
if dbByuser in dblist2:
  print("Veri tabanı var")
else:
  print("Yanlis oldu. Tekrar dene")
  dbname=client['23June_DB']
  print(dbname.list_collection_names())
  collectionName=dbname['students']
  ##mydata=collectionName.find({"bedrooms":{"$gt":5}},{"bedrooms":1,"name":1})
  mydata=collectionName.find()
  or i in mydata:
   print(i)
   item1= {
    "name":"Furkan",    
    "surname":"yumsak",
    "age":27
}
studentCol=dbname['students']
studentCol.insert_one(item1)
myStudentData=studentCol.find()
for i in myStudentData:
  print(i)
  studentCol2=dbname['students']
employees=studentCol2['Employees']
myEmployeesList= [
    {"name": "Yağmur", "surname":"Doğan"},
    {"name": "Güler", "surname": "Duman"},
    {"name":"Kaan", "surname": "Güçlü"}
]
employees.insert_many(myEmployeesList)
myEmployeesData=employees.find()
for i in myEmployeesData:
  print(i)
  Bir öğrenci otomasyonu yapalım. Öğrenciler önce kayıt olsun,sonra sisteme giriş yapsın.
print("##### ÖĞRENCİ OTOMASYON SİSTEMİ #####")
username = input("Kullanıcı adınızı giriniz")
password = input("Şifrenizi giriniz")
item= {
    "username":username,
    "password":password
}
unidb=client['students']
accountCollection=unidb['Accounts']
accountCollection.insert_one(item)
accountCollection.delete_one({"username":"kaangc"})
result=employees.delete_many({"name":"Güler"})
print(result.deleted_count)
employees.update_one({"name":"Kaan"},{"$set":{"name":"kadir"}})
myEmployeesData=employees.find()
for i in myEmployeesData:
  print(i)
  #collection silme
  employees.drop()
  #collection duracak tüm verileri silme  
  employees.deleted_many()
  #DB'yi silmek. Ancak bunun için MongoDB'de admin yetkisi tam olmalıdır yani tüm yetkileri açık olmalıdır.
