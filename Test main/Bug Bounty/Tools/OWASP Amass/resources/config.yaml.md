---
share: "true"
#mode: "passive"
mode: "active"
output_directory: "amass"
maximum_dns_queries: "20000"
resolver: "1.1.1.1 ; Cloudflare"
resolver: "8.8.8.8 ; Google"
resolver: "64.6.64.6 ; Verisign"
resolver: "74.82.42.42 ; Hurricane Electric"
resolver: "1.0.0.1 ; Cloudflare Secondary"
resolver: "8.8.4.4 ; Google Secondary"
resolver: "64.6.65.6 ; Verisign Secondary"
resolver: "77.88.8.1 ; Yandex.DNS Secondary"
address: "192.168.1.1"
cidr: "192.168.1.0/24"
asn: "26808"
port: "80"
port: "443"
port: "8080"
domain: "owasp.org"
domain: "appsecusa.org"
domain: "appsec.eu"
domain: "appsec-labs.com"
subdomain: "education.appsec-labs.com"
subdomain: "2012.appsecusa.org"
#local_database: "true ; Set this to false to disable use of the local database."
# postgres://[username:password@]host[:port]/database-name?sslmode: "disable of the PostgreSQL"
#primary: "false ; Specify which graph database is the primary db, or the local database will be selected."
#url = "postgres://[username:password@]host[:port]/database-name?sslmode: "disable""
#options="connect_timeout: "10""
# [username:password@]tcp(host[:3306])/database-name?timeout: "10s"
#url = [username:password@]tcp(host[:3306])/database-name?timeout: "10s"
#enabled: "true"
#recursive: "true"
#minimum_for_recursive: "1"
#wordlist_file: "/usr/share/wordlists/all.txt"
#wordlist_file: "/usr/share/wordlists/all.txt # multiple lists can be used"
#enabled: "true"
#edit_distance: "1 ; Setting this to zero will disable this expensive feature."
#flip_words: "true   # test-dev.owasp.org -> test-prod.owasp.org"
#flip_numbers: "true # test1.owasp.org -> test2.owasp.org"
#add_words: "true    # test.owasp.org -> test-dev.owasp.org"
#add_numbers: "true  # test.owasp.org -> test1.owasp.org"
#wordlist_file: "/usr/share/wordlists/all.txt"
#wordlist_file: "/usr/share/wordlists/all.txt"
data_sources:
  minimum_ttl: "1440 ; One day"
  #data_source: "Ask"
  #data_source: "Exalead"
  #data_source: "IPv4Info"
  #ttl: "4320 ; Time-to-live value sets the number of minutes that the responses are cached."
  #apikey: "; Each data source uses potentially different keys for authentication."
  #secret: "; See the examples below for each data source."
data_sources.AlienVault:
data_sources.AlienVault.Credentials:
  apikey: "220e1ad232f152adacf7316375ed864444594c4a7954f9815e5d840ba0002b8d"
data_sources.BinaryEdge:
  ttl: "10080"
data_sources.BinaryEdge.Credentials:
  apikey: "6ebb7e91-213c-48e3-8b35-478c596cecd5"
  #ttl: "4320"
data_sources.Censys:
  ttl: "10080"
data_sources.Censys.Credentials:
  apikey: "f10eef4f-321d-4760-8i1a-0483d330116d"
  secret: "IN9knbgCLWOdt2kNa0gpYOXBeIyCGJp2"
data_sources.Chaos:
  ttl: "4320"
data_sources.Chaos.Credentials:
  apikey: "9ac3b2c4d71c0bab2cfdb713f67eb0cf551d97b858f36f222ea1ee6ecf51"
data_sources.Cloudflare:
data_sources.Cloudflare.Credentials:
  apikey: "b7f621d7182ty75a83a983ef97662eb3c8fb"
  #ttl: "4320"
  #ttl: "4320"
data_sources.GitHub:
  ttl: "4320"
data_sources.GitHub.accountname:
  apikey: "ghp_0TYeKJrY71IyFk0ao3egP8ufsNh1Eo01MPuG"
data_sources.Hunter:
data_sources.Hunter.Credentials:
  apikey: "049230586c9b51297a028f1693497f4b49c05cdc"
data_sources.IPinfo:
data_sources.IPinfo.Credentials:
  apikey: "78b765dexyz030d"
data_sources.NetworksDB:
data_sources.NetworksDB.Credentials:
  apikey: "42bde7cf-b465-4a16-88f5-3880bf21f577"
data_sources.PassiveTotal:
  ttl: "10080"
data_sources.PassiveTotal.Credentials:
  username: "parabsiddhesh"
  apikey: "8a5a3c1576d4b493e478da740b34f716e06856d55c3c1c0129c1c537fb63d436"
data_sources.ReconDev:
data_sources.ReconDev.free:
  apikey: "free-2a7621dd-e54a-4fi2-879f-8fc70160e2c5"
data_sources.SecurityTrails:
  ttl: "1440"
data_sources.SecurityTrails.Credentials:
  apikey: "UeqhEzGorOrBwxbJnJBjgkCzLFQM2HQa"
data_sources.Shodan:
  ttl: "10080"
data_sources.Shodan.Credentials:
  apikey: "UyoD9RDcRCtGmH8FRPg8r4kzgU1gw"
data_sources.Spyse:
  ttl: "4320"
data_sources.Spyse.Credentials:
  apikey: "f3976251-ee53-4241-a798-6f0e3a666f6e"
data_sources.URLScan:
data_sources.URLScan.Credentials:
  apikey: "8f43fd83-cd3f-4533-b732-dec05689ee2c"
data_sources.VirusTotal:
  ttl: "10080"
data_sources.VirusTotal.Credentials:
  apikey: "a4f716aea17f2cf43c134708c037e343d276e625f0e26c0a1535beb3dc4a9b37"
data_sources.WhoisXMLAPI:
data_sources.WhoisXMLAPI.Credentials:
  apikey: "at_OvKlVzpx8GN91hJVhIxYm21QsVffZ"
  #ttl: "1440"
  #ttl: "1440"
