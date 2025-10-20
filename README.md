# Vault custom scripts

This repo contains custom scripts for certain Vault operations :
- List Vault PKI certificates expiring soon
- Read raw Vault data 


## List Vault PKI certificates expiring soon

In the **Vault-PKI-KPIs** folder, run the **check-vault-pki-certs.sh** as below in order to print all certificates expiring in the next *EXPIRY_THRESHOLD_DAYS* (14 days by default) :
```bash
export VAULT_ADDR=https://127.0.0.1:8200
export VAULT_TOKEN=<token>
./check-vault-pki-certs.sh
```

The script generates an output CSV file named *vault-certificates-YYYYMMDD-HHMMSS.csv* containing all certificates


To test on a local vault instance, you can create a fake aborescence by running the script **setup-vault-pki-test.sh** as below, which create 5 subnamespaces (app1, app2, ...app5) for 5 teams (team1, team2, ...team5), each namespace containing one PKI secret engine and 2 certificates (one expiring in 7 days, the other in 30 days) :
```bash
export VAULT_ADDR=https://127.0.0.1:8200
export VAULT_TOKEN=<token>
./setup-vault-pki-test.sh
```


## Read raw Vault data 

To read Vault raw data (dangerous in production), add *raw_storage_endpoint=true* in your vault configuration file and reload Vault service.
Then run the **raw.sh** script in te **Vault-raw-data** folder as below :
```bash
export VAULT_ADDR=https://127.0.0.1:8200
export VAULT_TOKEN=<token>
./raw.sh
```
