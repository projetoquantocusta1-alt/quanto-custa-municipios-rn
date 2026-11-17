# Projeto Quanto Custa — Prefeituras e câmaras do Rio Grande do Norte

Quanto custam as câmaras municipais e as prefeituras dos municípios do Rio Grande do Norte, desde 2017, corrigido pela
inflação. Aparece na página única dos municípios: https://quantocustaum.com/quanto-custa-municipios/?uf=rn

Mesmo código do repositório da Bahia (quanto-custa-municipios-ba). Só muda o bloco "ESTADO" em `config.py` e o
bloco CFG no começo de `docs/uf.js`.

## Fontes
- **SICONFI (Tesouro Nacional)**: RREO, Anexo 2 (despesa por função), de cada prefeitura, a cada bimestre.
  A câmara é a função "Legislativa". Conferido com o TCE-CE (Fortaleza e Sobral, 2025): a Legislativa (com a parte
  intraorçamentária) é igual ao gasto da câmara, e o total sem a parte intraorçamentária é igual ao gasto total.
- **TSE**: eleitos de 2016, 2020 e 2024. **IBGE**: população. **Banco Central**: IPCA.

## Limitações (explicadas também no site, em "Como calculamos")
- Sem nota a nota, fornecedores e gabinetes do prefeito e do vice: só o TCE-RN tem, e o robô ainda não foi
  testado no site dele.
- O RREO traz o empenhado e o liquidado por função, não o pago.
- Prefeituras que não entregam o relatório ao Tesouro ficam fora do ano e são listadas no site.

## Robô
`python atualizar.py` (todo dia, GitHub Actions). `--semanal` também baixa TSE, IBGE e IPCA. `--so-montar` só refaz o site.
Uma consulta por segundo ao SICONFI.
