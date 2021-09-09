## SSH Anahtarı ile Sunucuya Parolasız Erişmek

> SSH anahtarı ile sunucuya paralarız erişmek için yapılması gereken ön adımları buradaki
[1](https://docs.liman.dev/sistem-yonetimi/kurulum/kurulum-sonrasi-temel-ayarlar/uzak-sunucuda-ssh-paketinin-kurulmasi), 
[2](https://docs.liman.dev/sistem-yonetimi/kurulum/kurulum-sonrasi-temel-ayarlar/ssh-ile-uzaktan-baglanti-kurmak),
[3](https://docs.liman.dev/sistem-yonetimi/kurulum/kurulum-sonrasi-temel-ayarlar/ssh-konfiguerasyon-ayarlarinin-yapilmasi)
linklerden takip ederek tamamlayabilirsiniz.

Kişisel bilgisayarınız üzerinde (Windows ya da bir GNU/Linux dağıtımı), 
> *Ben Windows üzerinde powershell uygulamasını kullandım.*

![1](https://user-images.githubusercontent.com/37108233/132659940-d837181e-01dc-48a2-96d0-8b4e21d3e960.PNG)

`ssh-keygen`

komutu ile ssh anahtarı oluşturulabilir. SSH anahtarını bir parola ile oluşturmak mümkündür ancak parola konulmazsa gönderilen sunuculara parolasız erişim imkanı tanır.
>*Enter'a basarak geçebilriz.*

```
Enter file in which to save the key (C:\Users\username/.ssh/id_rsa):
Enter same passphrase again:
Your public key has been saved in C:\Users\username/.ssh/id_rsa.pub.
SHA256:*************************** username@pc
+---[RSA 3072]----+
|..B+             |
|                 |
|o.o..            |
|+* ..         o  |
|+.o.    S.   . + |
|.  ... oo o . E o|
|..         . . + |
|+o +sssss     o  |
|+o*o.  *+o       |
+----[SHA256]-----+
```

### SSH anahtarının uzak sunucuya gönderilmesi

Burada GNU/Linux dağıtımları ve Windows işletim sistemi arasında fark bulunmaktadır.

### GNU/Linux için,

ssh-copy-id username@192.168.1.100
ssh username@192.168.1.100

kullanılabilir. Bunun yanında konfigürasyon dosyasındaki Host anahtar kelimesi de bu işlem için kullanılabilir. Örneği Liman sunucusu için,

ssh-copy-id limanmys
ssh limanmys

### Windows için,

Windows için de [konfigürasyon](https://docs.liman.dev/sistem-yonetimi/kurulum/kurulum-sonrasi-temel-ayarlar/ssh-konfiguerasyon-ayarlarinin-yapilmasi) dosyasındaki Host anahtar kelimesinin kullanılması mümkündür.

>Tekrar Windows powershell ile aşağıdaki komutu çalıştırıyoruz.

![2](https://user-images.githubusercontent.com/37108233/132661551-fa42549c-e0f1-4ae1-9a2a-87c88ed361e2.PNG)

`type $env:USERPROFILE\.ssh\id_rsa.pub | ssh limanmys "cat >> .ssh/authorized_keys"`

![3](https://user-images.githubusercontent.com/37108233/132661665-a9344bbe-5559-40a3-a182-1492d1f1b7c2.PNG)

`ssh limanmys`

Bu adımdan sonra artık sunucularınıza parolasız erişmeniz mümkün olacaktır. Erişmenin yanı sıra [VSCode SSH](https://dev.to/liman/eklenti-gelistirme-ortami-kurulumu-3ofm) eklentisini de parolasız kullanabilirsiniz.

> Yazının orjinali için [linke](https://docs.liman.dev/sistem-yonetimi/kurulum/kurulum-sonrasi-temel-ayarlar/ssh-anahtari-ile-sunucuya-parolasiz-erismek) tıklayın.
