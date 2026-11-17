# Protótipo do painel, Studio Thiago Santos

Protótipo **apenas visual** da tela inicial (Painel) do sistema de gestão do Studio Thiago Santos.
Tudo é fictício: números, nomes de parceiros e iniciais de alunos. Não há back-end, banco ou integração.

## Como abrir

Abra o `index.html` no navegador. Não precisa instalar nada. As fontes vêm do Google Fonts, e sem internet o navegador usa a fonte do sistema.

## O que o painel mostra

- Resumo do mês em uma frase e termômetro de saúde do negócio.
- "Precisa de você hoje": cobranças vencidas, relatórios pedidos, famílias sem retorno e inativos para recuperar.
- Indicadores: clientes ativos (meta de 100), receita do mês, inadimplentes, perdas em 3 meses, equipe e parcerias.
- Gráficos: receita prevista e recebida, receita por linha, clientes ativos com entradas e saídas, saúde da carteira, ocupação semanal das aulas, feedback aos pais, funil de novos alunos, motivos de saída, alunos por profissional e por plano.
- Seletor de período (3, 6 ou 12 meses), tema claro e escuro, tooltips nos gráficos.

## Navegação

Cada card leva ao menu que trata do assunto, já com o filtro aplicado (ex.: Inadimplentes abre Financeiro filtrado).
As demais telas são esboços que mostram o filtro recebido e o que cada menu vai conter.

| Menu | Previsto para |
|---|---|
| Clientes, Financeiro | semanas 3 a 5 |
| Recuperação | semanas 6 e 7 |
| Aulas, Equipe | semanas 8 e 9 |
| Feedback dos pais | semanas 10 a 12 |
| Parcerias | semana 13 |

## Responsividade

Notebook: menu lateral e grade de cards. Celular: barra de navegação inferior com menu "Mais", cards em uma ou duas colunas.

## Para virar o sistema real

Os dados ficam no topo do script (`dados fictícios`). No sistema real, o número de cada card e a lista da tela de destino devem usar a mesma consulta, para a contagem nunca divergir.
