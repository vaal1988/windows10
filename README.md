# windows10

clone repo:
 ```bash
git clone https://github.com/vaal1988/windows10.git
cd ./windows10
```

download iso:
```bash
wget -O ./iso/Win10_21H1_English_x64.iso https://tb.rg-adguard.net/dl.php?go=fb555f3a
```
run build:
 ```bash
export TMPDIR="/var/tmp"
export PACKER_IMAGES_OUTPUT_DIR="/var/tmp/"
packer build -only="qemu" windows10.json
```
