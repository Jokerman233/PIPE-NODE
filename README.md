# PIPE-NODE
PIPE NETWORK CDN PoP NODE GUIDE

Create Directory:
```bash
sudo mkdir -p /opt/dcdn

Download Pipe tool Binary from the URL you were provided via Mail ($PIPE-URL is where you'll insert the download link. into the double quote.):

sudo curl -L "$PIPE-URL" -o /opt/dcdn/pipe-tool

Download Node Binary from the URL you were provided via Mail ($DCDND-URL is where you'll insert the download link. into the double quote.):

sudo curl -L "$DCDND-URL" -o /opt/dcdn/dcdnd

Make Binary Executable:

sudo chmod +x /opt/dcdn/pipe-tool
sudo chmod +x /opt/dcdn/dcdnd

