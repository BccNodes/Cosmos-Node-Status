# Cosmos-Node-Status

# status
Bu sistem sizi jail veya inaktif durum hakkında telegram üzerinden uyaracaktır. Ayrıca size her saat başı node durumunuz hakkında kısa bilgi gönderir.

Talimatlar:

1. `@BotFather` ile telegram botu oluşturun, özelleştirin ve `get bot API token` ([nasıl yapılacağını bilmiyorsanız](https://www.siteguarding.com/en/how-to-get-telegram-bot-api-token)).

2.En az 2 grup oluşturun: `alarm` and `log`. Bunları özelleştirin, botunuzu sohbetlerinize ekleyin ve `get chats IDs` ([nasıl yapılacağını bilmiyorsanız](https://stackoverflow.com/questions/32423837/telegram-bot-how-to-get-a-group-chat-id)).

3. Sunucunuza bağlanın ve `mkdir $HOME/status/` ile `status` klasörü oluşturun.

4. Bu klasörde `cosmos.sh` dosyası oluşturmanız gerekir; `nano $HOME/status/cosmos.sh`. Herhangi bir değişiklik yapmanıza gerek yoktur `cosmos.sh` dosyası kullanıma hazırdır.
> Bu depoda `cosmos.sh` dosyasını bulabilirsiniz.

5. Düğüm bilgilerimizi tanımlamak için `cosmos.conf` dosyasına ihtiyacımız var; `nano $HOME/status/cosmos.conf` . Dosya içindeki bilgileri özelleştiriniz.
> `cosmos.conf.ornek` ve `curl.md` dosyalarını bu depoda bulabilirsiniz.

6. `jq` ve `bc` paketlerini kurunuz; `sudo apt-get install jq bc -y` .

7. Status klasörünüzün içine girip, ayarlarınızı görmek için `bash cosmos.sh` komutunu çalıştırın. Her şey doğru ise çıktı aşağıdaki gibi veya benzer olmalıdır: 

```
root@v1131623:~/status# bash cosmos.sh 
 
/// 2022-05-21 14:16:44 ///
 
pylons-testnet-3

sync >>> 373010/373010.
jailed > true.
 
/// 2022-05-21 14:16:48 ///
 
stafihub-public-testnet-2

sync >>> 512287/512287.
place >> 47/100.
stake >> 118.12 fis.

root@v1131623:~/status# 
```

8. `slash.sh` dosyamızı oluşturalım; `nano $HOME/status/slash.sh` .
> Bu depoda `slash.sh.ornek` dosyasını bulabilirsiniz.
9. Bazı kurallar ekleyin; `chmod u+x cosmos.sh slash.sh`.
10. Crontab'ı düzenleyin (1 numaralı seçeneği seçiyoruz); `crontab -e`.
> Bu depoda `crontab.ornek` dosyasını bulabilirsiniz.
11. Günlüklerinizi `cat $HOME/status/cosmos.log` veya `tail $HOME/status/cosmos.log -f` ile kontrol edebilirsiniz.
