# Protótipo do sistema, Studio Thiago Santos

Protótipo navegável do sistema de gestão do Studio Thiago Santos, publicado em https://pedroduefarias.github.io/prototipo-sistema-thiagosantos/.
Serve para o Thiago e a Helen verem as telas, opinarem e aprovarem antes de cada tela virar código no sistema real.
Tudo é fictício: números, nomes e iniciais de alunos. Não há back-end, banco ou integração. O que é feito nas telas vale só até recarregar a página.

## Como entrar

Senha `123` para todos os perfis. A tela de login mostra os acessos.

| E-mail | Perfil | Quem | O que vê |
|---|---|---|---|
| `admin` | Administrador | Thiago | Tudo |
| `gestor` | Gestor | Helen | Dashboard, Clientes, Financeiro, Recuperação, Parcerias. Não vê registros de aula nem plano terapêutico; vê a folha da equipe só como total. |
| `profissional` | Profissional | Marina | As próprias aulas, presença, registros e relatórios. Não vê o financeiro. |
| `pais` | Família | Mãe do Lucas Moura | Só o que foi liberado do próprio filho, mensalidades e recibos |

Páginas públicas, sem login: `#agendar?origem=instagram` (formulário de lead para a bio do Instagram), `#pre-matricula` e `#convite` (primeiro acesso da família).
O botão **?** na tela de login ensina a colocar o sistema na tela do celular (Android e iPhone).

## Versões

### 1.0 (atual): pagamentos controlados pela Gestora

No começo **não há gateway de pagamento**. O controle de "já pagou" e "em atraso" depende da Helen:

- O sistema gera a mensalidade de cada aluno todo mês, com o valor e o vencimento da matrícula.
- **Vencida** é automático: passou o vencimento sem pagamento registrado.
- A Helen cobra pelo WhatsApp (botão `wa.me`, mensagem pronta) com a **chave Pix do studio** e o valor, e pede o comprovante.
- **Paga** só acontece quando a Helen registra o pagamento (valor, data, forma e como confirmou: comprovante, extrato ou em mãos). Fica registrado quem registrou e quando.
- Uma vez por semana a Helen confere os pagamentos registrados com o extrato do banco (aba "Conferir extrato").

### Próximas versões: gateway de pagamento

Com um gateway (a escolher, por exemplo Asaas, Efí ou Mercado Pago; taxas a comparar):

- Pix com código único por mensalidade, para saber de quem é cada pagamento sem comprovante.
- Baixa automática quando o banco confirma (webhook), sem a Helen digitar.
- Lembretes automáticos antes do vencimento.
- Cartão com cobrança recorrente.

O registro manual continua existindo para dinheiro, transferência e casos fora do gateway.

## Dashboard personalizável

O Administrador toca em **Personalizar**, liga ou desliga os blocos, arrasta para mudar a ordem (no celular: tocar, segurar e arrastar) e escolhe e quais indicadores ficam no topo. **Restaurar padrão** volta ao modelo padrão, que segue o que painéis de gestão de clínicas e studios costumam mostrar primeiro: o que precisa de ação hoje, caixa (entradas e saídas), receita, inadimplência, retenção e funil de novos alunos.
No protótipo a escolha fica guardada no navegador; no sistema real, fica no usuário e vale em qualquer aparelho.

## Financeiro: entradas e saídas

- **Entradas**: mensalidades e lançamentos (eventos, loja, palestras, home care, consultoria).
- **Saídas** (aba Saídas): contas a pagar por categoria (equipe, aluguel, impostos, contas de consumo, material, marketing, contador e sistemas, taxas). A Helen lança cada conta; as **fixas** se repetem sozinhas todo mês; as de valor variável entram quando a conta chega. Uma conta só vira **paga** quando alguém registra o pagamento, com comprovante. O valor de cada profissional vem do cadastro: fixo, ou aulas dadas (presenças) × valor por aula.
- **Fluxo de caixa** (aba Fluxo de caixa): entradas, saídas e resultado mês a mês, com a previsão de fechamento do mês.
- A conferência semanal do extrato vale para os dois lados.

## De onde vem cada número

Cada card do Dashboard mostra a origem do dado (botão "Origem dos dados"). Com o botão desligado, a origem aparece ao passar o mouse sobre o card:

- **Automático**: sai sozinho de algo que já existe (matrícula, datas, agenda).
- **Depende de registro**: só fica certo se alguém da equipe registrar (presença, pagamento, saída com motivo).
- **Manual**: cadastro feito à mão (parcerias, lançamentos de eventos e loja).

O card **Pendências de registro** mostra o que falta registrar para os números ficarem certos.

## Como abrir localmente

Abra o `index.html` no navegador. Não precisa instalar nada.

## Identidade

O símbolo do studio foi redesenhado em vetor a partir de um print de baixa resolução (`assets/logo.svg`, `icons/`). Quando houver o arquivo oficial da marca, troque o desenho em `assets/logo.svg`, no `<symbol id="logo">` do `index.html` e nos ícones de `icons/`.

## Para virar o sistema real

Os dados fictícios são gerados no próprio script, com semente fixa, para serem sempre os mesmos. No sistema real, o número de cada card e a lista da tela de destino devem usar a mesma consulta, para a contagem nunca divergir.
