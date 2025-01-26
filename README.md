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

# SETUP THE DCDND NODE SYSTEMD SERVICE
**7.Sample Service File Creation:**
```bash
# Create service file using tee
sudo tee /etc/systemd/system/dcdnd.service << 'EOF'
[Unit]
Description=DCDN Node Service
After=network.target
Wants=network-online.target

[Service]
# Path to the executable and its arguments
ExecStart=/opt/dcdn/dcdnd \
                --grpc-server-url=0.0.0.0:8002 \
                --http-server-url=0.0.0.0:8003 \
                --node-registry-url="https://rpc.pipedev.network" \
                --cache-max-capacity-mb=1024 \
                --credentials-dir=/root/.permissionless \
                --allow-origin=*

# Restart policy
Restart=always
RestartSec=5

# Resource and file descriptor limits
LimitNOFILE=65536
LimitNPROC=4096

# Logging
StandardOutput=journal
StandardError=journal
SyslogIdentifier=dcdn-node


# Working directory
WorkingDirectory=/opt/dcdn

[Install]
WantedBy=multi-user.target
EOF
```
# OPEN PORTS
**8. Paste The Following Commands To Open Ports. don't worry if it's not enabled at the end, you're on track**
```bash
sudo ufw allow 8002/tcp
sudo ufw allow 8003/tcp
sudo ufw reload
```
#START NODE
**9. start your node usind this commands:**
```bash
sudo systemctl daemon-reload
sudo systemctl enable dcdnd
sudo systemctl start dcdnd
```
# GENERATE AND REGISTER WALLET
**10. To generate a Solana keypair, run the following command:**
```bash
/opt/dcdn/pipe-tool generate-wallet --node-registry-url="https://rpc.pipedev.network"
```
You will be prompted to enter an optional 12-word passphrase or you press enter and one will be generated for you. The keypair is saved to ~/.permissionless/key.json
  # DONE
