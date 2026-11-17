# paths wordlists

common.txt

directory-list-2.3-medium.txt        ()

raft-large-directories.txt        ()

raft-large-files.txt          ()

**to find**: find / -name "common.txt" -printf "%h\n"

extensions-compressed.fuzz.txt   ()

`Databases`

fuzz-Bo0oM.txt  ()

extensions-most-common.fuzz.txt   ()

httparchive_apiroutes_2026_02_27.txt (assetnote)

---

Discovery/Web-Content/common.txt

Discovery/Web-Content/api/api-endpoints.txt

**api**:

`Discovery/Web-Content/api/api-seen-in-wild.txt`

/home/kali/SecLists/Discovery/Web-Content/api/api-seen-in-wild.txt

---

```bash
find / -name "directory-list-2.3-medium.txt" -printf "%h\n"
```

while read -r target; do ffuf -you "$target/FUZZ" -w /home/kali/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt -H "X-Forwarded-For: 127.0.0.1" -H "X-Forwarded-Host: 127.0.0.1" -c -mc 200,301,302; done < pathdirtemplist.txt

```bash
ffuf -w /home/kali/SecLists/Discovery/Web-Content/api/api-seen-in-wild.txt -u "https://auth.bancoplata.mx/auth/api/v1/auth-flow/FUZZ" \
  -x socks5://localhost:9050 \
  -t 5 -rate 5 \
  -c -ac \
  -fc 404,403,401
```
