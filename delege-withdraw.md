Daha önce testnet-contract reposunu kullanmıştık. Bunu güncelleyeceğiz. Adımlar şu şekilde

```console
cd testnet-contract
git pull
yarn install
```

`git pull` sonrası hata alırsanız `git stash` yazıp tekrar deneyin.

Bize lazım olacak key.json dosyasını da şurdaki adımlardan halletmiştik.
https://github.com/ruesandora/Ar.io/blob/main/key.json.md

En az 500 Test IO token gerekiyor. Test IO tokenleri daha önce ArNS tarafına katıldıysanız cüzdanlara gönderildi.
Sıradaki adımlar şunlar

### DELEGATE STAKE AKTİF ETME VE PARAMETRELER

```
nano tools/update-gateway-settings.ts
```
`const label` ve `const fqdn` satırlarına // işareti koyun 

![image](https://github.com/neuweltgeld/agir_abiler/assets/101174090/0ea49fda-88c7-465a-842b-c54221a0d338)

Sonra aşağı inip bu satırların başındaki // işaretini kaldırın. Aktif olacak satırlardaki // işaretini kaldırıyoruz yani.
![image](https://github.com/neuweltgeld/agir_abiler/assets/101174090/12234a24-6d59-4def-92ee-87ea6d26a849)

Aşağıda da güncellemek istediklerimizin // işaretini kaldırıyoruz, diğerlerine yoksa da // yazın resimdeki gibi
![image](https://github.com/neuweltgeld/agir_abiler/assets/101174090/ba455c9e-9e97-45c6-87a2-61bd9f8d9265)

`ctrl + x + y` ile kaydedip çıkın.

```
yarn ts-node tools/update-gateway-settings.ts
```

15 dk sonra alttaki işleme geçin

### STAKE İŞLEMİ

```
nano tools/delegate-stake.ts
```

![image](https://github.com/neuweltgeld/agir_abiler/assets/101174090/8ce7fb2b-59b7-4036-b626-fc46edf7abef)


`const qty` yazan yere delege etmek istediğiniz token miktarını.

`const target` yazan yere de delege etmek istediğiniz gatewayin cüzdanını yazıyorsunuz.

`ctrl + x + y` ile kaydedip çıkın.

Bu komutlar işlem başına olan komutlar, yani diyelim ki delegasyonu 500 yapıp yolladınız, sonra 600e yükselteceksiniz.
Bunun için ikinci sefer düzenlerken 600 değil, 100 yazacaksınız.

```
yarn ts-node tools/delegate-stake.ts
```
Komutuyla çalıştırıyoruz.

15 dk sonra alttaki işleme geçin

### WITHDRAW İŞLEMİ
Bu sefer de fazla stake miktarını withdraw etmek istiyorsunuz
```
nano tools/decrease-delegate-stake.ts
```
`const qty` yazan yere withdraw etmek istediğiniz token miktarını.

`const target` yazan yere de tokeni withdraw etmek istediğiniz gatewayin cüzdanını yazıyorsunuz.

`ctrl + x + y` ile kaydedip çıkın.

```
yarn ts-node tools/decrease-delegate-stake.ts
```
Komutuyla çalıştırıyoruz.

İşlemler bu kadar. 

Aşağıdaki linkin sonundaki <Cüzdan_Adresi> kısmını adresiniz ile değiştirin ve işlemleri doğru yapıp yapmadığınızı göreceksiniz..  "valid": true olunca işlem doğru demektir.

```
https://dev.arns.app/v1/contract/bLAgYxAdX2Ry-nt6aH2ixgvJXbpsEYm28NgJgyqfs-U/<Cüzdan_Adresi>
```
