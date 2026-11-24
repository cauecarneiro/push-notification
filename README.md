# Estudo de push notifications

Estudo de push notifications no iPhone: registrar o app no APNs e ver o device token para testar envios.

Estudo · iOS 18.5+ · 2025

## O que faz
- Pede autorização para alerta, selo e som.
- Registra o aparelho no APNs e imprime o device token no console.
- Mostra o aviso mesmo com o app aberto (banner, lista, som e selo) e registra no console o título do aviso que a pessoa tocou.
- Inclui um arquivo `sample-push-notification.apns`, para arrastar para o simulador e simular um push.

## Meu papel
Estudo feito em grupo, com colegas. Este repositório guarda a minha cópia do projeto, de 08/10/2025.

## Como foi feito
- `CustomAppDelegate` (via `UIApplicationDelegateAdaptor`) chama `registerForRemoteNotifications()` e recebe o token em `didRegisterForRemoteNotificationsWithDeviceToken`.
- O mesmo delegate trata `UNUserNotificationCenterDelegate`: `willPresent` para mostrar o aviso com o app aberto e `didReceive` para o toque.
- O app não envia push. O envio é feito por fora, por uma ferramenta que fale com o APNs usando o token impresso.
- O arquivo `PushNotification.entitlements` declara o ambiente de desenvolvimento do APNs (`aps-environment`).

## Tecnologias
Swift, SwiftUI, UserNotifications e APNs.

## Como rodar
1. Abra `PushNotification/PushNotification.xcodeproj` no Xcode e escolha o seu time de desenvolvimento em Signing & Capabilities (é preciso uma conta de desenvolvedor Apple para push em aparelho real).
2. Rode num iPhone real, toque em "Request Notification Access" e copie o token do console.
3. Para testar sem conta paga, arraste `sample-push-notification.apns` para o simulador (o arquivo tem um campo com o bundle id do app).

---
Feito por Cauê Crillanovick · [portfólio](https://cauecarneiro.github.io/portfolio/) · [LinkedIn](https://www.linkedin.com/in/cau%C3%AA-carneiro)
