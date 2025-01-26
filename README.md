# PIPE-NODE
PIPE NETWORK CDN PoP NODE GUIDE

**1. Create Directory:**
```bash
sudo mkdir -p /opt/dcdn
```

 **2. Download Pipe tool Binary from the URL you were provided via Mail ($PIPE-URL is where you'll insert the download link. into the double quote.):**
```bash
sudo curl -L "$PIPE-URL" -o /opt/dcdn/pipe-tool
```
**3.Download Node Binary from the URL you were provided via Mail ($DCDND-URL is where you'll insert the download link. into the double quote.):**
```bash
sudo curl -L "$DCDND-URL" -o /opt/dcdn/dcdnd
```

**4.Make Binary Executable:**
```bash
sudo chmod +x /opt/dcdn/pipe-tool
sudo chmod +x /opt/dcdn/dcdnd
```
# NODE REGISTRATION
**5. Execute the command below to Log In to Generate Access Token:**
```bash
/opt/dcdn/pipe-tool login --node-registry-url="https://rpc.pipedev.network"
```
**6. Use the command below to generate a Pipe Network registration token:**
```bash
/opt/dcdn/pipe-tool generate-registration-token --node-registry-url="https://rpc.pipedev.network" --credentials-dir=/root/.permissionless
```
 This token is necessary for registering or re-registering nodes. follow the authentication process.Upon successful login, you will see the message: “Logged in successfully!” in your terminal.

# Setup the dcdnd node systemd service

