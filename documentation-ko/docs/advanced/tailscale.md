# Tailscale

:::info
이 문서는 **자체 호스팅(self-hosted)** Khoj에 여러 기기에서 안전하게 접속하려는 경우에만 유용합니다. [Khoj Cloud](https://app.khoj.dev)를 사용하고 있다면 이 문서가 **필요하지 않습니다**.
:::

[Tailscale](https://tailscale.com)은 [Wireguard](https://www.wireguard.com/)와 OAuth를 사용하여 개인 VPN 생성을 단순화합니다. 이를 통해 어디서든 자신의 기기에서 서비스를 호스팅하고 접속할 수 있습니다.
아래 설명은 휴대폰, 노트북 등에서 자체 호스팅 Khoj에 간단하고 안전하게 접속하는 한 가지 방법입니다.

### 최소 설정
1. [표준 절차](/get-started/setup)에 따라 선호하는 기기에 Khoj를 설치합니다.
2. [Tailscale](https://tailscale.com)에 가입하고 Khoj에 접속하려는 기기에 앱을 설치합니다. 보통 Khoj 서버, 휴대폰, 노트북이 여기에 포함됩니다. Khoj 서버의 Tailscale IP 주소를 기록해두세요.
3. 서버에서 `--host <your_server_tailscale_ip>` 플래그를 포함하여 Khoj를 시작합니다.
4. Tailscale 네트워크에 있는 모든 기기에서 `http://<your_server_tailscale_ip>:42110`을 열어 Khoj에 접속하세요!


### HTTPS 인증서
:::info
Tailscale은 Wireguard를 사용하여 기기 간의 트래픽을 암호화하고 라우팅합니다. 따라서 Tailscale을 사용하면 안전한 접속을 위해 HTTPS가 반드시 필요하지는 않습니다. Tailscale과 함께 HTTPS를 사용하는 것은 브라우저가 보안 경고를 표시하지 않게 하고, HTTPS가 활성화되지 않으면 클립보드 접근과 같은 특정 기능이 차단되는 것을 방지하는 데에만 유용합니다.
:::

1. Tailscale 관리 콘솔의 [DNS](https://login.tailscale.com/admin/dns) 페이지에서 [MagicDNS](https://tailscale.com/kb/1081/magicdns#enabling-magicdns)와 [HTTPS](https://tailscale.com/kb/1153/enabling-https)를 활성화합니다. 고유한 Tailscale 도메인 이름(보통 .ts.net으로 끝남)을 기록해두세요.
2. 다음 명령어를 실행하여 Khoj 서버용 HTTPS 인증서를 생성합니다:
   ```bash
   # 서버 이름이 'server'이고 tailnet이 'black-forest.ts.net'이라고 가정합니다.
   # 생성된 .crt 및 .key 파일의 경로를 기록해두세요.

   tailscale cert server.black-forest.ts.net
   ```
3. 표준 포트에서 HTTPS를 통해 Khoj를 제공하도록 시작합니다.
   ```bash
   sudo KHOJ_DOMAIN=server.black-forest.ts.net \
   khoj \
   --sslcert /path/to/your/tailscale.crt \
   --sslkey path/to/your/tailscale.key \
   --host=server.black-forest.ts.net \
   --port 443
   ```
4. 이제 개인 Tailscale 네트워크에 있는 모든 기기에서 `https://server.black-forest.ts.net`으로 Khoj에 접속할 수 있습니다!
