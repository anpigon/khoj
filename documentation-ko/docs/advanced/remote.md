# 원격 접속

기본적으로 자체 호스팅된 Khoj는 실행 중인 머신에서만 접근할 수 있습니다. 원격 머신에서 안전하게 접근하려면 다음을 수행하세요:
- 셸 또는 `docker-compose.yml`을 통해 `KHOJ_DOMAIN` 환경 변수를 원격으로 접근 가능한 IP 또는 도메인으로 설정하세요.
  예시: `KHOJ_DOMAIN=my.khoj-domain.com`, `KHOJ_DOMAIN=192.168.0.4`.
- Khoj 관리자 비밀번호와 `KHOJ_DJANGO_SECRET_KEY` 환경 변수가 안전하게 설정되었는지 확인하세요.
- [인증](/advanced/authentication)을 설정하세요.
- OS 및 네트워크 방화벽에서 Khoj 포트(기본값: 42110)에 대한 접근을 허용하세요.

:::warning[HTTPS 인증서 사용]
공개 인터넷을 통해 사용자 지정 도메인에 Khoj를 노출하려면 SSL 인증서 사용을 강력히 권장합니다. [Let's Encrypt](https://letsencrypt.org/)를 사용하여 도메인에 대한 무료 SSL 인증서를 얻을 수 있습니다.

HTTPS를 비활성화하려면 `KHOJ_NO_HTTPS` 환경 변수를 `True`로 설정하세요. 이는 Khoj가 보안된 사설 네트워크 뒤에서만 접근 가능한 경우 유용할 수 있습니다.
:::

:::info[Tailscale 사용해보기]
[Tailscale](https://tailscale.com/)을 사용하여 네트워크를 통해 자체 호스팅된 Khoj에 쉽고 안전하게 접근할 수 있습니다.
1. `KHOJ_DOMAIN`을 머신의 [Tailscale IP](https://tailscale.com/kb/1452/connect-to-devices#identify-your-devices) 또는 [Tailnet의 FQDN](https://tailscale.com/kb/1081/magicdns#fully-qualified-domain-names-vs-machine-names)으로 설정하세요. 예: `KHOJ_DOMAIN=100.4.2.0` 또는 `KHOJ_DOMAIN=khoj.tailfe8c.ts.net`
2. Tailscale 네트워크의 모든 장치에서 `http://tailscale-ip-of-server:42110` 또는 `http://fqdn-of-server:42110`을 열어 Khoj에 접근하세요.
:::