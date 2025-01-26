# PIPE-NODE
PIPE NETWORK CDN PoP NODE GUIDE

1. Create Directory:
```bash
sudo mkdir -p /opt/dcdn
```

**Download Pipe tool Binary from the URL you were provided via Mail ($PIPE-URL is where you'll insert the download link. into the double quote.):**
```bash
sudo curl -L "$PIPE-URL" -o /opt/dcdn/pipe-tool
```
**Download Node Binary from the URL you were provided via Mail ($DCDND-URL is where you'll insert the download link. into the double quote.):**
```bash
sudo curl -L "$DCDND-URL" -o /opt/dcdn/dcdnd
```
**Make Binary Executable:**
```bash
sudo chmod +x /opt/dcdn/pipe-tool
sudo chmod +x /opt/dcdn/dcdnd
```
