# Kodarsivi Crud Kontrol Paneli Sistemi

Özellikle geliştiricilerin faydalanabileceği paketler ve kullanımlarını örnekleyerek hazırlanmıştır.

### Sistemi Oluşturan Bölümler

- Kontrol Paneli
- Ayarlar
    + Site Ayarları
    + Hakkımızda Ayarları
- Kullanıcılar
    + Kullanıcı Listesi
    + Kullanıcı Ekle
    + Yetki Listesi
    + Yetki Ekle
- Sayfalar
    + Sayfa Listesi
    + Sayfa Ekle
- Yazılar
    + Yazı Kategori Listesi
    + Yazı Kategori Ekle
    + Tüm Yazılar
    + Yayınlanmış Yazılar
    + Taslak Yazılar
    + Yazı Ekle
- Galeriler
    + Galeri Kategori Listesi
    + Galeri Kategori Ekle
    + Tüm Galeriler
    + Yayınlanmış Galeriler
    + Taslak Galeriler
    + Galeri Ekle
- Videolar
    + Video Kategori Listesi
    + Video Kategori Ekle
    + Tüm Videolar
    + Yayınlanmış Videolar
    + Taslak Videolar
    + Video Ekle
- Yorumlar
    + Tüm Yorumlar
    + Onaylanmış Yorumlar
    + Onaylanmamış Yorumlar
- İletişim
    + Tüm Mesajlar
    + Okunan Mesajlar
    + Okunmamış Mesajlar
  
  
### Kullanılan Paketler

- laravelcollective/html (https://laravelcollective.com/docs/6.0/html)
- spatie/laravel-permission (https://github.com/spatie/laravel-permission)
- intervention/image (http://image.intervention.io/)
- cviebrock/eloquent-sluggable (https://github.com/cviebrock/eloquent-sluggable)

Veritabanı tabloları Laravel `Database: Migrations` sistemi kullanılarak hazırlanmıştır.

Bu sayede veritabanı tablolarınızı kolaylıkla değiştirebilirsiniz ve yeni veritabanı tablolarınızı kolaylıkla sisteme dahil edebilirsiniz.

Örnekler için bakınız : https://laravel.com/docs/6.x/migrations

Laravel'de bulunan `Eloquent ORM`, veritabanınızla çalışmak için güzel ve basit bir aktif kayıt uygulaması sağlar.

Her veritabanı tablosunda, o tabloyla etkileşim kurmak için kullanılan bir `Model` bulunur.

Modeller, tablolarınızdaki verileri sorgulamanıza ve tabloya yeni kayıtlar eklemenize olanak tanır.

Örnekler için bakınız : https://laravel.com/docs/6.x/eloquent#introduction

Ayrıca sistemimizde `Eloquent: Relationships` kullanılarak veritabanı tabloları arasındaki ilişkiler kolaylıkla kurulmuştur.

Veritabanı ilişkileri için https://laravel.com/docs/6.x/eloquent-relationships adresteki ilişki örneklerini inceleyebilirsiniz.

Oluşturulan modeller ile veritabanımızdan okunan verileri yada veritabanına yazmak istediğimiz verileri Laravel Controller sistemiyle işlemekteyiz.

Sistemimizdeki tüm Controller Dosyaları CRUD Yapısına uygun oluşturulmuştur.

Laravel CRUD sisteminde extra oluşturulmuş yöntemler hariç 7 yöntem `(index,create,store,show,edit,update,destroy)` bulunur.

Laravel rotalarını kullanımımız crud yöntemiyle oluşturulmuş Controller dosyaları için
```php
Route::resource('/posts', 'PostController'); 
```
örneğindeki gibi kullanılmıştır.

Diğer Rotalar ise geliştiricilere kullanımda kolaylık sağlamak için isimlendirilmiştir.
```php
Route::get('publish', 'PostController@publish')->name('posts.publish'); 
```
örneğinde olduğu gibi.

İsimlendirilmiş rotaların kullanımı ve sağladığı kolaylıkları linkten inceleyebilirsiniz.
https://laravel.com/docs/6.x/routing#named-routes

Sistemdeki Form Alanlarında `laravelcollective/html` Paketi kullanılmıştır.
Bu paket size form alanlarını oluşturmakta kolaylıklar sağlayacaktır.

Sistem Üyelerine verilen Roller ve İzinler için `spatie/laravel-permission` Paketi kullanılmıştır.

Bu paket sayesinde tüm Controller alanlarında kullanıcının işleyeceği verilere kullanıcıya verilmiş olan izinlerle kısıtlamalar ekleyebiliriz.

Laravel Crud Sisteminin içerdiği yöntemlerle bunu `PostController` da örnekleyelim.

**İzinlerde Bulunan**
```
posts => index
posts-create => create,store
posts-show => show
posts-edit => edit,update
posts-destroy => destroy
```
Alanlarına erişim sağlayacak şekilde düzenlenmiştir.

Bu izinlerin kontrolü Controller Dosyalarımızda Laravel `Gate` methoduyla denetlenmektedir.

Örnek Olarak
```php
if (! Gate::allows('posts')) { return abort(401); }
```
`posts` alanımıza erişim izni olmayan bir kullanıcı 401 hatasını görüntüler.

Sistemdeki tüm alanlar mevcut yetki sistemiyle donatılmıştır.

Sizde yeni ekleyeceğiniz alanlara bu yetkileri kolaylıkla uygulayabilirsiniz.

Paket kullanımı ve paketin daha neleri içerdiğini https://github.com/spatie/laravel-permission adresinden görüntüleyebilirsiniz.

Sistemdeki resim yükleme ve işleme alanlarında ise `intervention/image` Paketi kullanılmıştır.

Bu paket sayesinde resimlerinizi istediğiniz gibi boyutlandırabilir kırpmalar yapabilir ve paketin size sağlamış olduğu birçok özellikten faydalanabilirsiniz.

Paket kullanımı ve paketin içerdiği özellikleri http://image.intervention.io/ adresinden görüntüleyebilirsiniz.

Sistemdeki Slug alanları için `cviebrock/eloquent-sluggable` Paketi kullanılmıştır.

Bu paket sayesinde tüm slug alanlarınızı kolaylıkla oluşturabilirsiniz.

İsterseniz Slug alanlarınızı benzersiz halede getirebilirsiniz.

Paket detayları ve kullanım örneklerini https://github.com/cviebrock/eloquent-sluggable adresinden görüntüleyebilirsiniz.

### Sistem Teması

Sistemde Metronic Bootstrap Teması Kullanılmıştır.

Metronic birçok geliştiricinin kullandığı çok popüler bir temadır.

Metronic in tema yapısını hiç bozmadan laravel e entegrasyonunu yapıp tüm çalışmamızı bu tema üzerinde yaptık.

Sizde Metronic in sunmuş olduğu tüm eklenti ve özellikleri sistem üzerinde geliştirmek istediğiniz alanlarda kullanabilirsiniz.

laravel-mix aracılığı ile tema sass dosyaları üzerinde yaptıgınız değişiklikleri direk olarak temaya uygulayabilir ve bu yapılan değişiklikleri izleyebilirsiniz.

laravel-mix ile ilgili detaylı kullanım örnekleri ve bilgiye https://laravel.com/docs/6.x/mix adresinden ulaşabilirsiniz.

#### Sistemde bazı alanlarda kullanıcıya kolaylıklar sağlamak için gelişmiş yöntemler kullandık.
Bunlardan bazıları
- Sayfalar alanında, kategoriler alanında, galeri kategoriler alanında ve video kategoriler alanında sürükle bırak ile düzenlenebilir sıra özelliği ve alt sayfa ve alt kategori özellikleri
- Yazılar,Galeriler ve Videolar alanlarındaki tablolarda Başlık bölümü Tıklama ile düzenlenebilmektedir.
- Galeri Resimlerinde açıklama bölümü, Yorumlarda Yorum alanı da tıklama ile düzenlenebilmektedir.
- Sayfalar, Yazılar, Galeriler, Videolar Alanlarındaki Tablolarda bulunan Yayınlanmış ve Taslak alanlarına tıklayarak içerik durumu değiştirilebilir.
- Yorumlarda yorum durumunu tabloda bulunan onaylanmış ve onaylanmamış butonlarına basarak güncelleme yapabilirsiniz.
- İletişim bölümünde mesaj durumunu tabloda bulunan okunmuş yada okunmamış butonlarına basarak güncelleyebilirsiniz.
- Tüm silme alanlarında Swetalert2 kullanılmıştır.
- Sistemde mevcut 2 dil (Türkçe,İngilizce) seçeneği vardır. bu seçenekleri istediğiniz gibi artırabilirsiniz.

### Sistem Kurulumu

Kurulum oldukça basittir.
İndirdiğiniz proje dosyaları dizininde ilk olarak
```bash
composer install
```
komutu ile projeye gerekli paketleri kolayca yükleyebilirsiniz.
Daha sonra
```bash
npm install
```
komutuyla projede gerekli npm paketlerini indirebilirsiniz.
ardından
```bash
npm run product
```
komuyuyla proje css ve js dosyalarını oluşturabilirsiniz.

Veritabanı dosyalarımızı oluşturmak için
Öncelikle `.env` Dosyasından veritabanı türü ve bağlantı seçeneklerini düzenleyip
```bash
php artisan migrate
```
komutuyla veritabanı dosyalarımızı oluşturabiliriz.
Mevcut veri tabanı içeriklerini aktarmak için ise
```bash
php artisan db:seed
```
Komutunu çalıştırınız.

Projeyi laravel geliştirme sunucusunda başlatmak için
```bash
php artisan serve 
```
Komutu kullanılır.


