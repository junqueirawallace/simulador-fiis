# Simulador de Investimentos em FIIs

## Sobre o projeto
Planilha educacional em Excel que simula a evolução de patrimônio a partir de aportes mensais e de uma taxa hipotética de rendimento. Também estima dividendos mensais e d distribui o aporte entre seis categorias de fundos imobiliários conforme o perfil selecionado.

> **Aviso:** valores e percentuais são exemplos fictícios para fins de aprendizagem. Rentabilidade e dividendos não são garantidos. Este projeto não constitui recomendação de investimento.

## Perguntas que a ferramenta responde
- **Quanto investir por mês?** Campo “Aporte mensal” na aba `Simulador`, configurado na aba `Configuracoes`.
- **Por quantos anos?** Campo “Prazo (anos)” e cenários de 2, 5, 10, 20 e 30 anos.
- **Qual a taxa de rendimento mensal?** Campo “Rendimento mensal”, configurado na aba `Configuracoes`.
- **Quanto patrimônio pode acumular?** Resultado principal e tabela de projeções na aba `Simulador`.
- **Quanto pode receber de dividendos por mês?** Estimativa calculada como patrimônio projetado multiplicado pela taxa mensal hipotética.

## Como funcionam as fórmulas
### VF
A função `VF` calcula o valor futuro de pagamentos periódicos. A fórmula usada é `=-FV(B7,B6*12,B5,0,0)`:
- `B7`: taxa mensal;
- `B6*12`: número de meses;
- `B5`: aporte mensal;
- primeiro `0`: valor presente inicial;
- último `0`: aportes ao fim de cada período.
O sinal negativo apresenta o patrimônio como valor positivo conforme a convenção de sinais das funções financeiras. O Excel pode mostrar os nomes localizados das funções conforme o idioma.

### PROCV
Na aba `Distribuicao`, cada linha contém uma chave composta `Perfil|Tipo de fundo`, por exemplo `Moderado|Papel`. A fórmula `=VLOOKUP($B$8&"|"&D13,Distribuicao!$A$3:$C$20,3,FALSE)` procura a combinação exata e retorna o percentual da terceira coluna.

## Intervalos nomeados
- `salario`: salário mensal fictício;
- `taxa_mensal`: taxa hipotética mensal;
- `percentual_sugerido`: percentual de salário para a sugestão;
- `prazo_anos`: prazo principal em anos;
- `aporte`: aporte mensal informado;
- `aporte_sugerido`: 30% do salário de exemplo.

## Percentuais por perfil
Percentuais definidos como **exemplos didáticos deste projeto**, não como recomendação de alocação. Cada perfil soma 100%.

| Tipo de fundo | Conservador | Moderado | Arrojado |
|---|---:|---:|---:|
| Tijolo | 15% | 25% | 35% |
| Papel | 35% | 25% | 15% |
| Híbridos | 20% | 15% | 15% |
| Fundos de fundos (FOFs) | 15% | 15% | 10% |
| Desenvolvimento | 5% | 10% | 15% |
| Logística | 10% | 10% | 10% |
| **Total** | **100%** | **100%** | **100%** |

## O que foi acrescentado/adaptado
- Três abas: `Simulador`, `Configuracoes` e `Distribuicao`;
- intervalos nomeados;
- simulação alternativa com 30% do salário;
- cenários de 2, 5, 10, 20 e 30 anos;
- lista suspensa de perfis;
- chave composta para busca via PROCV;
- gráfico de pizza da divisão do aporte;
- aviso educacional e valores fictícios.

## Como usar
1. Abra `simulador_fiis.xlsx` no Excel.
2. Na aba `Configuracoes`, altere os valores fictícios conforme desejar.
3. Na aba `Simulador`, selecione um perfil na célula B8.
4. Confira patrimônio, dividendos, projeções, divisão do aporte e gráfico.
5. Selecione cada perfil e confira que os percentuais somam 100%.

## Publicação no GitHub
Crie um repositório público com nome simples, por exemplo `simulador-fii-excel`. Envie `simulador_fiis.xlsx` e `README.md`. O link a entregar é o endereço do **repositório**, não o link direto para o arquivo.
