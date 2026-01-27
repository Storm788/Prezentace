# Bezpečnost v síťové komunikaci

**Kamila Milarová, Daniel Borovička, Kryštof Pavlů**

---

## Úvod

**Síťová komunikace** je proces výměny dat mezi více zařízeními v síti. Nejčastěji probíhá podle **modelu klient–server**, kde klient (např. prohlížeč) odesílá požadavek a server odpovídá na základě dostupných zdrojů a dat.

* Cílem síťové bezpečnosti je chránit citlivá data a zabránit neoprávněnému přístupu.
* Bezpečnost je klíčová, protože na internetu putují denně miliardy důležitých dat, včetně hesel, finančních informací a osobních údajů.

---

## Proč je bezpečnost důležitá

1. **Přenos citlivých dat**:
   - Online komunikace často zahrnuje osobní údaje, přihlašovací údaje, platební informace nebo důvěrné firemní informace.
2. **Hrozby odposlechu**:
   - Útočníci mohou během přenosu sledovat data (např. pomocí veřejné Wi-Fi).
3. **Riziko zneužití a krádeže identit**:
   - Pokud citlivé údaje získají útočníci, hrozí jejich zneužití.
   - Doplňujícím rizikem je ztráta dat a jejich manipulace, vedoucí k finančním nebo reputačním škodám.

---

## Komunikace klient–server

Klient–server komunikace je základním pilířem síťového přenosu dat.

* Klient odešle požadavek na server, například dotaz nebo žádost o přístup k obsahu.
* Server tento požadavek zpracuje a odpoví informací nebo službou.
* Data během přenosu putují napříč sítí přes různá zařízení, jako jsou routery, switche a brány.
* Proces má dvě základní podoby:
  - **Synchronní komunikace**: Klient čeká na odpověď serveru a nemůže dále pracovat.
  - **Asynchronní komunikace**: Klient mezitím pokračuje ve své činnosti a odpověď zpracovává až po jejím přijetí.

---

## Nešifrovaná komunikace a její rizika

Pokud data přenášená po síti nejsou šifrována, mohou být napadena a zneužita.

### Charakteristiky nešifrované komunikace
- Data jsou přenesena jako čitelný text.
- Útočníci mohou snadno odposlouchávat nebo manipulovat s obsahem.

### Útok typu MITM (Man-in-the-Middle)
- Útočník se neoprávněně dostane mezi klienta a server.
- Odposlouchává komunikaci, čte nebo upravuje data.
- Obeť si nemusí vůbec všimnout, že komunikace byla kompromitována.
- Tento útok je běžný na veřejných Wi-Fi nebo nezabezpečených síťových připojeních.

### Typické příklady nešifrované komunikace
- **HTTP** (protokol pro běžné webové stránky bez šifrování)
- **Čisté TCP sockety**, které nevyužívají žádné vrstvy ochrany.

---

## Šifrování dat

Šifrování je technologie, která chrání data tím, že je převádí do nečitelné podoby. Pouze osoby (nebo zařízení) disponující potřebným **klíčem** mohou tato data dešifrovat.

### Základní principy šifrování
1. **Šifrovací klíč**
   - Klíč slouží k šifrování i dešifrování dat.
   - Bez odpovídajícího klíče jsou data nepoužitelná.
2. **Použití šifrování**
   - Přenášení citlivých informací jako hesla, osobní údaje nebo důvěrná komunikace.
   - Ochrana před odposlechem a zneužitím.

### Typy šifrování
1. **Symetrické šifrování**
   - Používá jeden klíč pro šifrování i dešifrování.
   - Je rychlejší, ale méně bezpečné, protože klíč musí být sdílen mezi oběma stranami.
2. **Asymetrické šifrování**
   - Používá dvojici klíčů: veřejný (pro šifrování) a soukromý (pro dešifrování).
   - Je vhodné pro bezpečné přenášení dat, například v bankovnictví.
   - Vyžaduje vyšší výpočetní výkon než symetrické šifrování.
3. **TLS (Transport Layer Security)**
   - Moderní standard pro šifrování síťové komunikace, který kombinuje symetrické a asymetrické postupy.

---

## TLS a HTTPS

### TLS
- **TLS (Transport Layer Security)** poskytuje zabezpečení pro komunikaci na internetu.
- Chrání data před odposlechem i manipulací.
- Umožňuje bezpečné připojení k serverům, například k internetovým bankám nebo e-shopům.

### HTTPS
- **HTTPS (HyperText Transfer Protocol Secure)** je rozšíření klasického protokolu HTTP, které využívá šifrování TLS.
   - HTTPS zajišťuje důvěrnost a integritu dat při přenosu.
   - Ověřuje identitu serveru certifikátem.
- Typickým znakem HTTPS je ikona zámku u adresního řádku v moderních prohlížečích.

---

## Certifikáty a důvěra

Využívání certifikátů je základní prvek zajištění bezpečné komunikace.

1. **Certifikát serveru**
   - Certifikát obsahuje informace o totožnosti serveru (např. doménové jméno).
   - Slouží k ověření, že server je důvěryhodný.
2. **Certifikační autorita (CA)**
   - Důvěryhodná organizace může vydat certifikát po řádném ověření.
   - Certifikáty vydané CA jsou uznávány hlavními webovými prohlížeči.

---

## Hesla a autentizace

Autentizace je klíčovou součástí bezpečné komunikace. Většina moderních systémů přidává další ochranné vrstvy, aby zajistila, že uživatelská data a účty budou v bezpečí.

### Ochrana hesel
1. **Hash a Salt**
   - Hesla se nikdy neukládají v otevřené podobě – místo toho se hashují.
   - Používání saltu zabraňuje útokům pomocí předpočítaných tabulek (Rainbow Tables).
2. **Dvoufaktorové ověření (2FA)**
   - Další vrstva ochrany, která vyžaduje druhý faktor (např. SMS kód nebo biometrický údaj).

---

## Nezabezpečené a zabezpečené sockety

1. **Sockety v komunikaci**
   - Sockety slouží jako rozhraní pro výměnu dat mezi aplikacemi na různých počítačích.
   - Bezpečnost u klasických socketů není standardně zajištěna.

2. **Rizika nezabezpečených socketů**
   - Útočníci mohou získat přístup k přenášeným datům.
   - Data mohou být napadena nebo zcizena během přenosu.

3. **Zabezpečení pomocí TLS**
   - Šifrování dat po celou dobu přenosu.
   - Ověření totožnosti serveru.
   - Ochrana proti MITM útokům a jiným hrozbám.

---

## Shrnutí

1. **Nešifrovaná komunikace je riziková** – útočníci snadno odposlouchávají a manipulují s daty.
2. Používání **šifrování** dat pomocí TLS je dnes standardem.
3. **Bezpečnostní certifikáty** jsou klíčové pro důvěru mezi klienty a servery.
4. Bezpečnost **hesel a autentizace** je zajištěna hashováním a dvoufaktorovým ověřením.
5. **Integrované šifrování a ověřování** je nutnou součástí moderních aplikací a technologií.

Základní pochopení těchto principů je nevyhnutelné pro zajištění bezpečí na internetu. Zabezpečit komunikaci je nejen zodpovědnost vývojářů, ale i uživatelů.
