# read DB __ Create in DB

```bash
curl -s http://154.57.164.79:31489/api.php/city/london | jq
```

---

```bash
curl -X POST http://<SERVER_IP>:<PORT>/api.php/city/ -d '{"city_name":"HTB_City", "country_name":"HTB"}' -H 'Content-Type: application/json'
```

 Delete city

```bash
curl -X DELETE http://154.57.164.79:31489/api.php/city/leeds
```

Update a city's name to 'flag'::

```bash
curl -X PUT http://154.57.164.79:31489/api.php/city/london \
-H "Content-Type: application/json" \
-d '{"city_name": "flag", "country_name": "(UK)"}'
```

Search for the city named 'flag'::

```bash
curl -s http://154.57.164.79:31489/api.php/city/flag | jq
```
