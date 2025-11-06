# r_2024_projudi_custompdf2excel

| 🇬🇧 **English** | 🇧🇷 **Português** |
|---|---|
| **Summary (💡)** — R Markdown pipeline that converts irregular **Projudi-like PDFs** (where common converters fail) into a clean, analyzable table and exports it to **Google Sheets**. | **Resumo (💡)** — Pipeline em **R Markdown** que converte **PDFs irregulares tipo Projudi** (quando conversores comuns falham) em uma tabela limpa e exporta para o **Google Sheets**. |
| **Business value (📈)** — Enables audit/reconciliation and quick KPIs by turning unstructured statements into structured data, replacing manual copy-paste. | **Valor de negócio (📈)** — Permite auditoria/conciliação e KPIs rápidos ao transformar extratos não estruturados em dados estruturados, substituindo o copia-e-cola manual. |
| **Tech stack (⚙️)** — R 4.2+, `rmarkdown`, `pdftools`, `tidyverse` (`dplyr`, `tidyr`, `readr`), `googlesheets4`. | **Stack técnico (⚙️)** — R 4.2+, `rmarkdown`, `pdftools`, `tidyverse` (`dplyr`, `tidyr`, `readr`), `googlesheets4`. |
| **Costs (💰)** — Local compute + Google Sheets API (free tier). | **Custos (💰)** — Computação local + Google Sheets API (faixa gratuita). |

## Data dictionary / Dicionário de dados (📚)

| 🇬🇧 **English** | 🇧🇷 **Português** |
|---|---|
| Columns parsed from lines (spacing-based): `Nro. Estabelecimento`, `Identificador`, `Data Transação`, `Modalidade`, `Bandeira`, `Nr Parcelas`, `Arquivo`, `Nr Linha`, `Inconsistência Encontrada`, `Valor Bruto`, `Valor Líquido`, `Taxa Praticada`, `Taxa Contratada`, `Valor Líquido Corrigido`, `Valor a Ressarcido`.* | Colunas extraídas das linhas (baseado em espaçamentos): `Nro. Estabelecimento`, `Identificador`, `Data Transação`, `Modalidade`, `Bandeira`, `Nr Parcelas`, `Arquivo`, `Nr Linha`, `Inconsistência Encontrada`, `Valor Bruto`, `Valor Líquido`, `Taxa Praticada`, `Taxa Contratada`, `Valor Líquido Corrigido`, `Valor a Ressarcido`.* |
| *Names may vary slightly depending on the PDF version. | *Os nomes podem variar ligeiramente conforme a versão do PDF.|

## Run locally / Execução local (sem CSV, apenas Sheets)

| 🇬🇧 **English** | 🇧🇷 **Português** |
|---|---|
| 1) Put the source PDF under `data_raw/` (not versioned). | 1) Coloque o PDF fonte em `data_raw/` (não versionado). |
| 2) Open `notebooks/Planilha LP 1588.Rmd` (or your Rmd) in RStudio and **Knit**. | 2) Abra `notebooks/Planilha LP 1588.Rmd` (ou seu Rmd) no RStudio e dê **Knit**. |
| 3) Configure Google Sheets: set env vars in a local (non-versioned) `.Renviron`: | 3) Configure o Google Sheets: defina variáveis em um `.Renviron` local (não versionado): |
| `GSHEET_ID=your_sheet_id_here`<br>`GSHEET_SHEET=exp` | `GSHEET_ID=seu_sheet_id_aqui`<br>`GSHEET_SHEET=exp` |
| 4) The Rmd will authenticate (`googlesheets4`) and write the parsed table to the configured Sheet. | 4) O Rmd autenticará (`googlesheets4`) e escreverá a tabela parseada na planilha configurada. |

## Repo structure / Estrutura do repositório

```
r_2024_projudi_custompdf2excel/
├─ src/               # (opcional) código de produção
├─ notebooks/         # exploração e protótipos (Rmd)
├─ reports/           # prints, GIFs, e atalho .gsheet (sem CSV)
├─ tests/             # (opcional)
├─ .gitignore
├─ README.md
└─ DESCRIPTION / renv.lock / (opcional)
```

## Deploy

| 🇬🇧 **English** | 🇧🇷 **Português** |
|---|---|
| Local utility now. Can be wrapped later as a `plumber` API or `shiny` app if needed. | Utilitário local por enquanto. Pode virar uma API `plumber` ou app `shiny` depois, se necessário. |

## Checklist (✅)

- [ ] Estrutura limpa e `.gitignore` conforme regras fixas.  
- [ ] README 🇬🇧🇧🇷 side-by-side completo.  
- [ ] Screenshot/GIF “antes → depois” em `reports/`.  
- [ ] **Release `v1.0.0`** publicada.  
- [ ] **Pin** na organização **hamburgcap**.  
- [ ] Dados e atalhos do Drive **não versionados** (`data/`, `*.gsheet`, `*.gdoc`).  

---

**Next step / Próximo passo:** criar a release `v1.0.0` e fixar o repo na org.  
**Qual será o próximo projeto?** 🚀
