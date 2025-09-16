
# Легенда
🟨 Процес/Етап · 🟦 Контроли/PAT · 🟩 Качество/QC · 🟥 CCP/Риск · 🟪 Данни/Проследимост · 🟫 Опаковка/Студена верига

---

## Диаграма 1 — End-to-End (E2E) поток
```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#fff2b2','lineColor':'#555','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  A[MCB/WCB<br/>Клетъчни банки] --> B[Seed Train<br/>Thaw→RM→STR]
  B --> C[Перфузия HFB<br/>масив кухи влакна]
  C --> D[Harvest<br/>тъкан]
  D --> E[Assembly<br/>ядлив скафолд + mould]
  E --> F[Сол/Подправки/Дим<br/>профил Rodopa]
  F --> G[Охлаждане/Стабилизация]
  G --> H[QC Release<br/>микро/ендотоксини/сензорика]
  H --> I[Опаковка<br/>Vacuum/VSP или MAP]
  I --> J[Студена верига<br/>0–4°C]
  J --> K[Дистрибуция/3PL<br/>GS1 EPCIS събития]
  K --> L[Ритейл/HORECA]

  B -.-> Bc[(PAT:<br/>pH/DO/Glc/Lac)]
  C -.-> Cc[(PAT:<br/>Debit/DO/Temp)]
  H -.-> Hd[(QA/QC:<br/>панели/граници)]
  I -.-> Id[(Етикет/1169/2011)]
  K -.-> Kd[(EPCIS 2.0:<br/>GTIN/LOT/GLN/SSCC)]

  classDef proc fill:#fff2b2,stroke:#555,color:#222;
  classDef pat fill:#b2d7ff,stroke:#355,color:#122;
  classDef qc fill:#b6f2c2,stroke:#274,color:#143;
  classDef data fill:#d7c2ff,stroke:#534,color:#312;
  class A,B,C,D,E,F,G,H,I,J,K,L proc;
  class Bc,Cc pat; class Hd qc; class Id,Kd data;
````

```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#fff2b2','lineColor':'#555','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  A[MCB/WCB<br/>Клетъчни банки] --> B[Seed Train<br/>Thaw→RM→STR]
  B --> C[Перфузия HFB<br/>масив кухи влакна]
  C --> D[Harvest<br/>тъкан]
  D --> E[Assembly<br/>ядлив скафолд + mould]
  E --> F[Сол/Подправки/Дим<br/>профил Rodopa]
  F --> G[Охлаждане/Стабилизация]
  G --> H[QC Release<br/>микро/ендотоксини/сензорика]
  H --> I[Опаковка<br/>Vacuum/VSP или MAP]
  I --> J[Студена верига<br/>0–4°C]
  J --> K[Дистрибуция/3PL<br/>GS1 EPCIS събития]
  K --> L[Ритейл/HORECA]

  B -.-> Bc[(PAT:<br/>pH/DO/Glc/Lac)]
  C -.-> Cc[(PAT:<br/>Debit/DO/Temp)]
  H -.-> Hd[(QA/QC:<br/>панели/граници)]
  I -.-> Id[(Етикет/1169/2011)]
  K -.-> Kd[(EPCIS 2.0:<br/>GTIN/LOT/GLN/SSCC)]

  classDef proc fill:#fff2b2,stroke:#555,color:#222;
  classDef pat fill:#b2d7ff,stroke:#355,color:#122;
  classDef qc fill:#b6f2c2,stroke:#274,color:#143;
  classDef data fill:#d7c2ff,stroke:#534,color:#312;
  class A,B,C,D,E,F,G,H,I,J,K,L proc;
  class Bc,Cc pat; class Hd qc; class Id,Kd data;
````

<div style="page-break-after: always"></div>

---

## Диаграма 2 — Seed Train & Банкиране

```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#fff2b2','lineColor':'#555','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  S0[WCB ампула] --> S1[Размразяване<br/>37°C/асептика]
  S1 --> S2[Първична експанзия<br/>шейк фласки]
  S2 --> S3[RM 5–50 L<br/>rocking-motion]
  S3 --> S4[STR N-2<br/>50–200 L]
  S4 --> S5[STR N-1<br/>200–500 L]
  S5 --> S6[Инокулиране N<br/>производство]

  S2 -.-> Q2[Микоплазма(−)]
  S3 -.-> Q3[Viab ≥90%]
  S4 -.-> Q4[Стерилност(−)]
  S5 -.-> Q5[Спец. растеж стабилен]

  classDef proc fill:#fff2b2,stroke:#555,color:#222;
  classDef qc fill:#b6f2c2,stroke:#274,color:#143;
  class S0,S1,S2,S3,S4,S5,S6 proc;
  class Q2,Q3,Q4,Q5 qc;
```

<div style="page-break-after: always"></div>

---

## Диаграма 3 — Перфузионен модул (HFB) и PAT

```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#fff2b2','lineColor':'#555','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  H0[Медия (SFM)<br/>резервоар] -->|перфузия| H1[HFB касети<br/>микроциркулация]
  H1 --> H2[Тъканен блок<br/>сантиметрова дебелина]
  H2 --> H3[Събиране/Harvest]

  H1 -.-> P1[(DO)]
  H1 -.-> P2[(pH)]
  H1 -.-> P3[(Дебит/налягане)]
  H1 -.-> P4[(Температура)]
  H0 -.-> P0[(Филтрация/стерилност)]

  H0 ==> C0((CCP:<br/>стерилни конектори))
  H1 ==> C1((CCP:<br/>целост HFB))
  H2 ==> C2((CCP:<br/>граници DO/pH))

  classDef proc fill:#fff2b2,stroke:#555;
  classDef pat fill:#b2d7ff,stroke:#355;
  classDef ccp fill:#ffb3b3,stroke:#a33,stroke-width:2px;
  class H0,H1,H2,H3 proc; class P0,P1,P2,P3,P4 pat; class C0,C1,C2 ccp;
```

<div style="page-break-after: always"></div>

---

## Диаграма 4 — Assembly върху ядлив скафолд (суджук/колбас)

```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#fff2b2','lineColor':'#555','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  A0[Мускулна фаза] --> A2[Смес]
  A1[Мастна фаза]  --> A2
  A2 --> A3[Ядлив скафолд<br/>ориентирана порестост]
  A3 --> A4[Mould форма<br/>суджук геометрия]
  A4 --> A5[Сол/Подправки]
  A5 --> A6[Дим/Сушене]
  A6 --> A7[Охлаждане]

  A3 -.-> QA1[Механика/адхезия]
  A4 -.-> QA2[Форма/диаметър]
  A6 -.-> QA3[a_w / pH граници]

  classDef proc fill:#fff2b2,stroke:#555;
  classDef qc fill:#b6f2c2,stroke:#274;
  class A0,A1,A2,A3,A4,A5,A6,A7 proc; class QA1,QA2,QA3 qc;
```

<div style="page-break-after: always"></div>

---

## Диаграма 5 — Опаковка и етикетиране (Vacuum/VSP или MAP)

```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#fff2b2','lineColor':'#555','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  P0[Порциониране] --> P1[Вакуум/VSP]
  P0 --> P2[MAP O2/CO2/N2]
  P1 --> P3[Етикет 1169/2011]
  P2 --> P3
  P3 --> P4[Shelf-life тестове]
  P4 --> P5[Освобождаване партида]

  P2 -.-> N1[Без CO в MAP]
  P3 -.-> N2[GTIN/LOT/алергени]
  P4 -.-> N3[Микро/оксидативни маркери]

  classDef proc fill:#fff2b2,stroke:#555;
  classDef note fill:#d7c2ff,stroke:#534;
  class P0,P1,P2,P3,P4,P5 proc; class N1,N2,N3 note;
```

<div style="page-break-after: always"></div>

---

## Диаграма 6 — Студена верига и дистрибуция

```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#fff2b2','lineColor':'#555','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  C0[Хладилен склад<br/>0–4°C] --> C1[3PL транспорт<br/>темп. логери]
  C1 --> C2[Дистрибутор]
  C2 --> C3[Ритейл / HORECA]
  C3 --> C4[Потребител]

  C1 -.-> CT1[Отклонение? → CAPA]
  C2 -.-> CT2[Случайни проверки]
  C3 -.-> CT3[FIFO/FEFO]

  classDef proc fill:#fff2b2,stroke:#555;
  classDef qc fill:#b6f2c2,stroke:#274;
  class C0,C1,C2,C3,C4 proc; class CT1,CT2,CT3 qc;
```

<div style="page-break-after: always"></div>

---

## Диаграма 7 — Данни и проследимост (GS1 / EPCIS 2.0)

```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#d7c2ff','lineColor':'#534','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  D0[GTIN<br/>Продукт] --> D1[LOT/Batch]
  D1 --> D2[GLN<br/>Локация/Обект]
  D1 --> D3[SSCC<br/>Логист. единици]
  D2 --> D4[EPCIS събития<br/>Commission/Ship/Receive]
  D3 --> D4
  D4 --> D5[Recall Query<br/>GTIN+LOT→маршрут]

  classDef data fill:#d7c2ff,stroke:#534,color:#111;
  class D0,D1,D2,D3,D4,D5 data;
```

<div style="page-break-after: always"></div>

---

## Диаграма 8 — HACCP карта: опасности → CCP и контроли

```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#ffb3b3','lineColor':'#a33','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  H01[Опасност:<br/>микробна контаминация] --> CC1((CCP:<br/>асептично инокулиране))
  H02[Опасност:<br/>микоплазма] --> CC2((CCP:<br/>тест преди RM/STR/N))
  H03[Опасност:<br/>ендотоксини/остатъци] --> CC3((CCP:<br/>валидирано отмиване))
  H04[Опасност:<br/>структурен дефект] --> CC4((CCP:<br/>HFB профил))
  H05[Опасност:<br/>пост-процес контаминация] --> CC5((CCP:<br/>опаковка/шевове))
  H06[Опасност:<br/>студена верига] --> CC6((CCP:<br/>температури/логери))

  CC1 --> CT1[Мониторинг:<br/>sUS конектори]
  CC2 --> CT2[qPCR/ензимни тестове]
  CC3 --> CT3[LAL тренд-контрол]
  CC4 --> CT4[PAT: DO/дебит/темп]
  CC5 --> CT5[Leak test/метал-детектор]
  CC6 --> CT6[Алгоритъм за аларми/FEFO]

  classDef ccp fill:#ffb3b3,stroke:#a33,stroke-width:2px;
  classDef ctrl fill:#b6f2c2,stroke:#274;
  class H01,H02,H03,H04,H05,H06 ccp;
  class CC1,CC2,CC3,CC4,CC5,CC6 ccp;
  class CT1,CT2,CT3,CT4,CT5,CT6 ctrl;
```

<div style="page-break-after: always"></div>

---

## Диаграма 9 — OT/SCADA сегментация (IEC 62443 / NIST 800-82)

```mermaid
flowchart TB
  Z0[Enterprise IT<br/>(ERP/PLM)]:::it --> Z1[DMZ<br/>(Hist/EPCIS/API)]:::dmz
  Z1 --> Z2[ICS Network<br/>SCADA/MES]:::ics
  Z2 --> Z3[Cell/Area<br/>PLC/RTU/Sensors]:::cell
  Z3 --> Z4[Field IO<br/>pH/DO/Debit/Temp]:::field

  Z0 -.Segmentation.-> Z1
  Z1 -.Zones/Conduits.-> Z2
  Z2 -.RBAC/Whitelists.-> Z3
  Z3 -.Secure Protocols.-> Z4

  classDef it fill:#e8eefe,stroke:#667;
  classDef dmz fill:#f2efe2,stroke:#775;
  classDef ics fill:#eaf7ea,stroke:#474;
  classDef cell fill:#fff5e6,stroke:#864;
  classDef field fill:#fbe6f0,stroke:#845;
```

<div style="page-break-after: always"></div>

---

## Диаграма 10 — Риск → Контрол (решаваща мапа)

```mermaid
%%{init: {'theme':'base','flowchart':{'htmlLabels':true,'curve':'linear'},'themeVariables':{'primaryColor':'#b6f2c2','lineColor':'#274','textColor':'#222','fontSize':'14px'}} }%%
flowchart TB
  R1[Разход на медии] --> M1[Serum-Free оптимизация<br/>локални входове]
  R2[Дебелина/масообмен] --> M2[HFB масиви<br/>DoE профили]
  R3[Приемливост/маркетинг] --> M3[Фрейминг „култивирано Rodopa“<br/>шеф дегустации]
  R4[LCA/енергия] --> M4[Зелена енергия<br/>рециклиране на среда]
  R5[Контаминация] --> M5[HACCP CCP<br/>CIP/SIP + sUS]

  classDef risk fill:#ffd1d1,stroke:#a33;
  classDef mit fill:#b6f2c2,stroke:#274;
  class R1,R2,R3,R4,R5 risk; class M1,M2,M3,M4,M5 mit;
```
