CVE => Common Vulnerability Exposure

 2024-13918

References :
1- https://www.cvedetails.com
2- https://cve.mitre.org/cve/search_cve_list.html
3- https://www.exploit-db.com

1- verify operating system
2- verify releases or service information
3- verify open ports
4- verify services and version information

192.168.1.1 => nmap -O =>( linux ) => nmap -A => (Linux Debian 10) => Port scan => 9050
=> Tor => Vulnerable =>  epxloit

specify the exploit to use
1- every exploit can work only for one operating system
2- every exploit can work only for one specify service version
3- every exploit can work only with specific privilege
4- every exploit has its own risk score

to search for cve with Metasploit

> search "CVE-2008-4250"

Can use searchsploit to search for vulnerabilities related to service or operating system
`
# searchsploit "windows xp"

to get more information about specific exploit

## searchsploit -p <id of expliot>

## apt install snapd
## systemctl start snapd
## systemctl enable snapd
## export PATH=/snap/bin:$PATH

https://hossamshady.medium.com/search-for-cves-now-1f8897c1d711
