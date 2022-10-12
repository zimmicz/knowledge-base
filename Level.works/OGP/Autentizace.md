# Autentizace
- Amplify se konfiguruje podle domény (ogp x hq) -> tohle je potřeba udělat dřív, než se k tomu vůbec někde začne přistupovat
- ``<Authenticator />; 
	- se renderuje tam, kde je potřeba přistupovat k auth objektu (nejlíp pomocí useAuthenticator hooku)