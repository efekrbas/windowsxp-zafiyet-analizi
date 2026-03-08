# Windows XP Zafiyet Analizi

İlk olarak netdiscover kullanarak ağda cihaz taraması yaptım 

<img width="945" height="279" alt="image" src="https://github.com/user-attachments/assets/cba415e5-38f7-4482-b14e-eaa528138cd1" />

Yaptığım tarama sonucunda varsayılan makine IP'lerimden farklı olarak 192.168.138.130 numaralı bir IP adresi keşfettim

192.168.138.130 numaralı IP adresine nmap taraması gerçekleştirdim

<img width="945" height="384" alt="image" src="https://github.com/user-attachments/assets/7316b3fc-66cd-405e-a430-e48f449e372c" />

 
Toplanan bilgiler ışığında, Windows XP sistemlerdeki en kritik servis zafiyetlerinden biri olan MS08-067 (NetAPI) açığı hedef alınmıştır. Bu işlem için Metasploit Framework kullanılmıştır.
Modül: exploit/windows/smb/ms08_067_netapi
Yapılandırma: Hedef IP (RHOSTS) olarak 192.168.138.130 ve saldırgan IP (LHOST) olarak 192.168.138.128 belirlenmiştir. Payload olarak windows/meterpreter/reverse_tcp seçilmiştir.
Sonuç: exploit komutu çalıştırıldıktan sonra zafiyet başarıyla tetiklenmiş ve hedef sistem üzerinde bir Meterpreter oturumu açılmıştır.
3. Yetki Doğrulama ve Erişim
Sisteme erişim sağlandıktan sonra elde edilen yetki seviyesi kontrol edilmiştir.
Doğrulama: getuid komutu çalıştırıldığında, sistemdeki en yüksek yetki seviyesi olan NT AUTHORITY\SYSTEM cevabı alınmıştır.
Erişim: Bu sonuç, parolasız ve tam yetkili bir şekilde işletim sisteminin tamamen kontrol altına alındığını kanıtlamaktadır.

<img width="945" height="231" alt="image" src="https://github.com/user-attachments/assets/80fe401d-508e-4bb7-bd0e-aade71613d80" />


 
Meterpretere eriştikten sonra cd komutuyla C dizinine geçtim ve ls komutuyla dosyaları listeledim flag.txt adlı bir dosya olduğunu farkettim ve cat komutuyla içinde yazan yazıya ulaştım.

<img width="945" height="401" alt="image" src="https://github.com/user-attachments/assets/cfb4ce65-9ef7-47f7-ada2-ab4ef06438aa" />

 
Ardından hashdump komutuyla kullanıcıların MD5 hash'lerine eriştim.

<img width="945" height="140" alt="image" src="https://github.com/user-attachments/assets/3909070f-d637-4815-8264-bef0174758d2" />

 
screenshot komutunu kullanarak hedef makinenin anlık ekran görüntüsünü aldım.

<img width="827" height="106" alt="image" src="https://github.com/user-attachments/assets/86654230-c8d6-4155-abba-4ba588de127a" />
<br><br>
<img width="945" height="598" alt="image" src="https://github.com/user-attachments/assets/9d8e25d4-f2f2-48e5-8072-db08a6477ec4" />

 
 

Screenshare komutuyla hedef makineyi tarayıcı üzerinden canlı olarak izlemeyi elde ettim.

<img width="842" height="163" alt="image" src="https://github.com/user-attachments/assets/7428e6f9-7f6a-4ac8-93a4-8a8c4426e35c" />

 
Clearev komutu ile sistem loglarını temizledim

<img width="799" height="148" alt="image" src="https://github.com/user-attachments/assets/6f6ab6d8-449a-4cad-876a-79847387b8e2" />

 
