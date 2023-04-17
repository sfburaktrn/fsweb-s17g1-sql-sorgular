# SQL Sorgu Alıştırmaları

Bu hafta SQL sorguları üzerine çalışıyorsunuz. Bugünkü alıştırmada sizin için hazırladığımız veritabanında aşağıda istediğimiz sonuçları elde etmenize yarayan SQL sorgularını oluşturacaksınız.

# Proje Kurulumu

Projeyi forklayın ve clonlayın. Tamamladığınızda da pushlayın.

## Kütüphane Bilgi Sistemi

Bu veritabanı, bir okulun kütüphanesinden öğrencilerin aldıkları kitapların bilgisini barındırmaktadır.

#Tablolar
`ogrenci` tablosu öğrencilerin listesini tutar.
`islem` tablosu öğrencilerin kütüphaneden aldıkları kitapların bilgilerini tutar
`kitap` tablosu kütüphanedeki kitapların bilgisini tutar
`yazar` tablosu kitapların yazarları bilgisini tutar
`tur` tablosu kitapların türlerini tutar.

Tablo ilişiklerini görmek için [ktphn.png] dosyasına göz atın.

Yazdığınız sorguları buradan test edebilirsiniz: [https://ergineer.com/assets/materials/fkg36so5-kutuphanebilgisistemi-sql/] (update, delete, drop sorguları iptal edilmiştir).

### Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını altlarına yazın.

    1) ÖRNEK SORU: Öğrenci tablosundaki tüm kayıtları listeleyin.

    	CEVAP: select * from ogrenci


    2) Öğrenci tablosundaki öğrencinin adını ve soyadını ve sınıfını listeleyin.

       Cevap: SELECT ograd, ogrsoyad, sinif FROM ogrenci

    3) Öğrenci tablosundaki kız öğrencileri listeleyin.

       Cevap:SELECT * FROM ogrenci where cinsiyet="K"

    4) Öğrenci tablosunda kaydı bulunan sınıfların adını her sınıf bir kez görüntülenecek şekilde listeleyiniz

       Cevap:  SELECT DISTINCT sinif FROM ogrenci

    5) Öğrenci tablosunda, 10A sınıfında olan kız öğrencileri listeleyiniz.

       Cevap: SELECT * FROM ogrenci where sinif="10A" AND cinsiyet="K"

    6) Öğrenci tablosundaki 10A veya 10B sınıfındaki öğrencilerin adını, soyadını ve sınıfını listeleyiniz.

       Cevap: SELECT ograd, ogrsoyad,sinif FROM ogrenci where sinif="10A" OR sinif="10B"

    7) Öğrenci tablosundaki öğrencinin adını, soyadını ve numarasını okul numarası olarak listeleyiniz. (as kullanım örneği)

       Cevap:SELECT ogrenci.ograd, ogrenci.ogrsoyad, ogrno AS OkulNumarasi FROM ogrenci

    8) Öğrenci tablosundaki öğrencinin adını ve soyadını birleştirip, adsoyad olarak listeleyiniz. (concat, as kullanım örneği)

       Cevap: SELECT CONCAT(ograd, ' ' , ogrsoyad) AS adsoyad FROM ogrenci;

    9) Öğrenci tablosundaki Adı ‘A’ harfi ile başlayan öğrencileri listeleyiniz.

       Cevap: SELECT * FROM ogrenci where ograd like "A%"
    10) Kitaplar tablosundaki sayfa sayısı 50 ile 200 arasında olan kitapların adını ve sayfa sayısını listeleyiniz.

       Cevap: SELECT kitapadi,sayfasayisi FROM kitap where sayfasayisi BETWEEN 50 AND 200

    11) Öğrenci tablosunda adı Fidan, İsmail ve Leyla olan öğrencileri listeleyiniz.

       Cevap: SELECT * FROM ogrenci where ograd IN ("Fidan", "İsmail","Leyla")
    12) Öğrenci tablosundaki öğrencilerden adı A, D ve K ile başlayan öğrencileri listeleyiniz.

       Cevap: SELECT * FROM ogrenci WHERE ograd LIKE "A%" OR ograd LIKE "D%" OR ograd LIKE "K%"

    13) Öğrenci tablosundaki sınıfı 9A olan Erkekleri veya sınıfı 9B olan kızların adını, soyadını, sınıfını ve cinsiyetini listeleyiniz.

       Cevap: SELECT ograd, ogrsoyad, sinif, cinsiyet FROM ogrenci
              WHERE (sinif = "9A" AND cinsiyet = "E") OR (sinif = "9B" AND cinsiyet = "K")
    14) Sınıfı 10A veya 10B olan erkekleri listeleyiniz.

       Cevap:SELECT * FROM ogrenci WHERE sinif IN ("10A", "10B") AND cinsiyet = "E";

    15) Öğrenci tablosunda doğum yılı 1989 olan öğrencileri listeleyiniz.

       Cevap: SELECT * FROM ogrenci WHERE dtarih = 1989;

    16) Öğrenci numarası 30 ile 50 arasında olan Kız öğrencileri listeleyiniz.

       Cevap: SELECT * FROM ogrenci WHERE ogrno between 30 and 50 AND cinsiyet="K"


    17) Öğrencileri adına göre sıralayınız (alfabetik).

       Cevap: SELECT * FROM ogrenci order by  ograd

    18) Öğrencileri adına, adı aynı olanlarıda soyadlarına göre sıralayınız.

       Cevap:SELECT * FROM ogrenci order by  ograd , ogrsoyad

    19) 10A sınıfındaki öğrencileri okul numarasına göre azalan olarak sıralayınız.

       Cevap:SELECT * FROM ogrenci  where sinif="10A" order by  ogrno desc

    20) Öğrenciler tablosundaki ilk 10 kaydı listeleyiniz.
    [İPUCU: `Select top tüm mysql versiyonlarında düzgün çalışmaz. LİMİT kullanmak daha faydalıdır`]

        Cevap: SELECT * FROM ogrenci LIMIT 10

    21) Öğrenciler tablosundaki ilk 10 kaydın ad, soyad ve doğum tarihi bilgilerini listeleyiniz.

        Cevap:SELECT ograd, ogrsoyad, dtarih FROM ogrenci LIMIT 10

    22) Sayfa sayısı en fazla olan kitabı listeleyiniz.

        Cevap: SELECT max(sayfasayisi) AS SayfaSayısıEnFazla FROM kitap

    23) Öğrenciler tablosundaki en genç öğrenciyi listeleyiniz.

        Cevap:SELECT * FROM ogrenci  order by dtarih desc LIMIT 1

    24) 10A sınıfındaki en yaşlı öğrenciyi listeyin.

        Cevap: SELECT* FROM ogrenci WHERE dtarih=(select min(dtarih) FROM ogrenci WHERE sinif="10A")

    25) İkinci harfi N olan kitapları listeleyiniz.

        Cevap:SELECT * FROM kitap WHERE kitapadi like "_n%"

    26) Öğrencileri sınıflarına göre gruplayarak listeleyin.

        Cevap: SELECT ograd AS AD , ogrsoyad AS SOYAD, sinif AS SINIF FROM ogrenci group by sinif,ograd,ogrsoyad

    27) Öğrencileri her sorgulamada sıralaması farklı olacak şekilde rastgele listeleyin.
    [İPUCU: rand() fonksiyonu]

        Cevap: SELECT * FROM ogrenci order by rand()

    28) Öğrenci tablosundan Rastgele bir öğrenci seçiniz.

        Cevap:SELECT * FROM ogrenci order by rand() LIMIT 1

    29) 10A sınıfından rastgele bir öğrencinin adını, soyadını, numarasını ve sınıfını getirin.

        Cevap:SELECT ograd,ogrsoyad,ogrno,sinif FROM ogrenci WHERE sinif='10A' order by rand() LIMIT 1

    # Esnek
    30) Öğrenci tablosunda aynı isimde kaçar öğrenci olduğunu bulmak istiyoruz.
    Öğrenci isimlerinin sayısını "adet" olarak öğrencilerin isimleri "isim" olarak listeleyin.
    [İPUCU: count() ve group by]

        Cevap: SELECT count(ograd) as adet,
    		ograd as isim FROM ogrenci
    		group by ograd
