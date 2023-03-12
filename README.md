# Q-Blockchain Node Tutorial

### SOURCE:
- https://docs.q.org/how-to-setup-validator/
## Install Node


## Create Password Wallet
```
cd ~/testnet-public-tools/testnet-validator
nano keystore/pwd.txt
```
**simpan CTRL+XY lalu ENTER**
## Create Wallet
```
docker run --entrypoint="" --rm -v $PWD:/data -it qblockchain/q-client:testnet geth account new --datadir=/data --password=/data/keystore/pwd.txt
```
### Claim Faucet
- https://faucet.qtestnet.org/

## Edit File .env
```
nano.env
```
- QCLIENT_IMAGE = ganti dengan 1.2.3
- ADDRESS = isi address kalian tanpa 0x
- IP = isi IP VPS kalian
- Dibawah BOOTNODE3 Tambahkan:
```
BOOTNODE4_ADDR=enode://85d6f24920a0f552a5e0360366d18fb1234880c4370f257abc09e8ec762173fb3c4b1b14a7af9a23a8c31751b3ba2905d6a98fb436dfe3092644527a89046977@3.68.108.12:30303
BOOTNODE5_ADDR=enode://ec40af9079c53e880f7e783ae5053b18d1f8bb8cd55b2dfbbfa3b7e1f5256c724ef7e22f23f785c2f119fbb7930769540e3c01c711c6ae26c83690b941a4886c@85.215.92.83:30303
BOOTNODE6_ADDR=enode://1032c556fbbfe37761951a20c2b98b4031234a8f871cc79dd8ff612a3e0436afe3458b325d2f25617b62134cfc8a8a4885e80c9760ecb4bb7c8deaee67a098ae@95.217.169.172:30303
BOOTNODE7_ADDR=enode://e974d9354ababd356a6bfecbb03a59d14ab715ffa02d431c6accfc5de250e9c8c345817bd5687c119a04df78f1a4673e97877ea5775fa84270d311dac4a2eca7@128.199.213.70:30313
```
**simpan CTRL+XY lalu ENTER**
## Edit File .json
```
nano config.json
```
- Address = Isi address kalian tanpa 0x
- Password = isi password yang dah dibuat, jika lupa pake command cek password cat `keystore/pwd.txt`
**Simpan CTRL+XY lalu ENTER**
## Stake Contract
```
docker run --rm -v $PWD:/data -v $PWD/config.json:/build/config.json qblockchain/js-interface:testnet validators.js
```
## Daftar Validator
```
nano docker-compose.yaml
```
Pada bagian setelah "geth" tambahkan
```
"--ethstats=NAMA_VALIDATOR:TESTNET_ACCESS_KEY@stats.qtestnet.org",
```
Nama_validator ganti dengan ITN kalian pas waktu daftar.
```
docker compose up -d
```
```
Cek Log Node
```

## Done. Cek node kalian:
- https://stats.qtestnet.org/
