# IF-BrA — Índice de Funcionalidade Brasileiro Aplicado

Ferramenta web para avaliação de funcionalidade e determinação do grau de deficiência para fins de aposentadoria especial, conforme a **Lei Complementar 142/2013** e a **Portaria Interministerial MPS/SDH/MF/MOG/AGU nº 1/2014**.

## Sobre

O IF-BrA é um instrumento padronizado utilizado por peritos médicos e assistentes sociais do INSS para classificar o grau de deficiência (grave, moderado ou leve) de segurados que requerem aposentadoria da pessoa com deficiência.

A aplicação implementa a escala completa de 41 atividades distribuídas em 7 domínios funcionais, incluindo o modelo de lógica fuzzy linguística para ajuste de pontuações em domínios sensíveis.

## Domínios Avaliados

| Domínio | Atividades |
|---------|-----------|
| 1. Sensorial | Visão, Audição |
| 2. Comunicação | Receber/produzir mensagens, conversação, discussão, dispositivos remotos |
| 3. Mobilidade | Posicionamento corporal, manipulação de objetos, movimentos de mãos, locomoção |
| 4. Cuidados Pessoais | Higiene, cuidados corporais, continência, vestir-se, alimentação, saúde |
| 5. Vida Doméstica | Preparo de refeições, tarefas domésticas, cuidar de pertences e de outros |
| 6. Educação e Trabalho | Educação, treinamento, trabalho remunerado, compras, gestão financeira |
| 7. Socialização e Vida Comunitária | Regulação comportamental, regras sociais, relacionamentos, cidadania |

## Sistema de Pontuação

Cada atividade recebe uma das quatro pontuações:

- **100** — Independente: realiza sem adaptação, em velocidade e segurança normais
- **75** — Adaptado/Modificado: realiza de forma adaptada ou mais lenta, sem dependência de terceiros
- **50** — Assistência de Terceiros: necessita de preparação, supervisão ou auxílio
- **25** — Dependência Total: não realiza ou é realizada inteiramente por terceiros

### Classificação de Gravidade (LC 142/2013)

Com base na pontuação combinada de dois avaliadores (máximo 8.200):

| Grau | Pontuação |
|------|-----------|
| Grave | ≤ 5.739 |
| Moderado | 5.740 – 6.354 |
| Leve | 6.355 – 7.584 |
| Insuficiente | ≥ 7.585 |

## Lógica Fuzzy

O aplicativo implementa o modelo de lógica fuzzy linguística para quatro tipos de deficiência:

- **Auditiva** — domínios sensíveis: Comunicação, Socialização
- **Intelectual/Cognitiva/Mental** — domínios sensíveis: Vida Doméstica, Socialização
- **Motora** — domínios sensíveis: Mobilidade, Cuidados Pessoais
- **Visual** — domínios sensíveis: Mobilidade, Vida Doméstica

Quando as três condições de ativação são atendidas simultaneamente, a menor pontuação dos domínios sensíveis é aplicada a todas as atividades desses domínios.

## Tecnologias

- **React 18** (via CDN)
- **Babel Standalone** (transpilação JSX no navegador)
- **jsPDF** + **AutoTable** (geração de relatórios PDF)
- **CSS3** com variáveis customizadas
- **localStorage** para persistência de rascunhos

## Como Usar

Nenhuma instalação ou build é necessário. Basta abrir o arquivo `index.html` em um navegador moderno:

```bash
# Abrir diretamente
open index.html

# Ou via servidor HTTP local
python -m http.server 8000
# Acesse: http://localhost:8000
```

### Fluxo de uso

1. Preencha a identificação do participante e do avaliador
2. Configure o modelo de lógica fuzzy (opcional)
3. Avalie cada uma das 41 atividades nos 7 domínios
4. Visualize os resultados com pontuações e classificação legal
5. Exporte o relatório em **PDF**, **CSV** ou **JSON**

## Exportação

- **PDF** — Relatório formatado com metadados, resumo de pontuações e detalhamento por item
- **CSV** — Dados tabulares com pontuações por domínio e por item
- **JSON** — Payload estruturado completo com todas as informações da avaliação

## Licença

Este projeto implementa o instrumento oficial de avaliação definido pela legislação brasileira (LC 142/2013).
