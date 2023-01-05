# Hangi Twitter Kullanıcısı En Çok Hangi Konularda Tweetliyor
   Buradaki amacımız istediğimiz bir Twitter kullanıcısının (hesabı gizli olmayacak) en çok hangi konularda tweetler attığını görebilmektir. Bu sayede istediğimiz kulanıcının hangi konular üzerinde daha çok ilgilendiğini ve bu konularda nelerden bahsettiğini görebileceğiz.
   Yüklemiş olduğum bu Python kodu, belli bir Twitter kullanıcısının son 2000 tweetini alır ve bunlar arasından benzer olanları tespit etmek için KMeans yöntemini kullanır. KMeans yöntemi, verilen tweetleri belirli bir sayıda gruba (kümelere) ayırır ve her grup içinde benzer tweetleri bir arada tutar. Kodun çalışma biçimini özetleyecek olursak;
1.	İlk olarak, Twitter kullanıcısının tweetlerini ve tweetlerle ilgili bilgileri (tweet içeriği, tarih, beğenme sayısı vb.) toplamak için snscrape   kütüphanesini kullanır. Bu kütüphane sayesinde, belli bir kullanıcının tweetlerini bir liste olarak alırız.
2.	Daha sonra, bu tweetlerden istenilen sayı kadarını (burada 2000 tweet) bir pandas veri çerçevesine (dataframe) atarız.
3.	Tweetlerin içeriğini temizlemek için bir fonksiyon yazılır. Bu fonksiyon, tweetleri lowercase hale getirir, URL'leri siler, punctuation karakterlerini çıkartır ve kelimelere ayrılır. Daha sonra, tweetlerdeki kelimelerden stopwords (çok sık kullanılan ve anlamı olmayan kelimeler) çıkartılır. Bunun yanı sıra, kendi oluşturduğumuz bir stopwords listesiyle tweetlerdeki belirli kelimeler de çıkartılır.
4.	Temizlenen tweetler kontrol amaçlı oluşturulan cleanedtweets.csv isimli dosyayada kontrol edilir.
5.	Temizlenen tweetleri tekrar veri çerçevesine atarız ve TfidfVectorizer kullanarak tweetleri vektörize ederiz. TfidfVectorizer, verilen metinleri sayısal değerler dizisi olarak ifade eden bir yöntemdir. Böylece, tweetler arasındaki benzerlikleri daha kolay tespit etmemizi sağlar.
6.	Vektörize edilen tweetleri KMeans yöntemiyle belirli bir sayıda gruba (kümelere) ayırırız. Bu kodta, küme sayısı 5 olarak belirlenmiştir.
7.	Ayırılan grupların ortalama vektörlerini kelimelere çevirir ve bu kelimeleri grupların oluşturulma kriterleri olarak kullanırız.


