Programação para Dispositivos Móveis (PPDM)
Tópicos 01 e 02 — Dispositivos Móveis & Criação de Interface

📝 Parte 1: Respostas Conceituais
1. Diferença de Arquiteturas: Nativo vs Cross-Platform/Híbrido
O desenvolvimento Nativo (Android com Kotlin/Java ou iOS com Swift/Objective-C) usa a linguagem e o SDK oficial de cada plataforma, compilando diretamente para código de máquina daquele sistema. Isso garante o máximo de performance e acesso total às APIs nativas do dispositivo, mas exige manter dois códigos-fonte separados (um para Android, outro para iOS), o que aumenta o custo e o tempo de desenvolvimento.
Já o desenvolvimento Cross-Platform/Híbrido, como o Flutter, permite escrever um único código-fonte (em Dart, no caso do Flutter) que é compilado para rodar em múltiplas plataformas (Android, iOS, Web, Desktop). O Flutter, especificamente, não usa componentes de UI nativos da plataforma — ele desenha cada widget diretamente na tela através de sua própria engine gráfica (Skia/Impeller), o que garante consistência visual entre plataformas e boa performance, embora ainda possa exigir "pontes" (platform channels) para acessar certas funcionalidades nativas específicas.
Resumo da diferença principal: Nativo = um código por plataforma, acesso total ao SDK nativo, maior custo de manutenção. Cross-Platform = um código para todas as plataformas, menor custo e maior velocidade de desenvolvimento, com pequenas limitações de acesso a recursos muito específicos do sistema.
2. StatelessWidget vs StatefulWidget
No Flutter, tudo é um Widget — desde um simples texto até o layout completo da tela. Existem dois tipos principais:
StatelessWidget: é um widget imutável. Uma vez construído, suas propriedades não mudam ao longo do tempo. Ele não guarda nenhum estado interno; se algo precisar mudar, o widget inteiro precisa ser reconstruído a partir de um widget pai.
Exemplo de uso: um ícone, um texto estático, um logo, um botão cujo texto e aparência nunca mudam (ex: `Text("Bem-vindo ao app")`).
StatefulWidget: é um widget que possui um estado mutável (representado por uma classe `State` associada). Ele pode ser reconstruído dinamicamente em resposta a interações do usuário ou mudanças de dados, sem precisar recriar toda a árvore de widgets ao redor.
Exemplo de uso: um contador que incrementa a cada clique, um formulário com campos de texto, um checkbox que alterna entre marcado/desmarcado, uma lista de favoritos que pode crescer.
Regra prática: se o widget precisa "lembrar" de algo e mudar visualmente sem intervenção externa, ele é Stateful. Se ele só exibe informações fixas ou recebidas de fora (via construtor), ele é Stateless.
3. O que acontece quando chamamos `setState()`?
Quando `setState()` é chamado dentro de um `StatefulWidget`, o Flutter:
Executa a função passada como parâmetro, que normalmente atualiza uma ou mais variáveis internas do estado (ex: `contador++`).
Marca aquele widget como "sujo" (dirty), avisando o framework de que ele precisa ser reconstruído.
O Flutter chama novamente o método `build()` daquele widget, gerando uma nova árvore de widgets (na verdade, uma nova descrição da UI).
O Flutter compara essa nova árvore com a anterior (usando o algoritmo de diffing da árvore de elementos/render objects) e atualiza somente as partes da tela que realmente mudaram, sem redesenhar a interface inteira do zero.
Ou seja, `setState()` não altera a tela diretamente — ele avisa o framework que o estado mudou e "agenda" uma reconstrução eficiente da UI para refletir esse novo estado.

💻 Parte 2: Prática Hands-on
[ ] Tutorial oficial concluído: Flutter Getting Started — Step 3
[ ] Árvore de widgets construída com `Scaffold`, `Row`, `Column` e `Container`
[ ] Interatividade e alteração de estado implementadas (`StatefulWidget` + `setState()`)
[ ] Código organizado em componentes separados (widgets próprios em arquivos distintos)
[ ] App testado sem erros e sem overflow de tela
Link do repositório GitHub: adicionar aqui

✅ Critério de Aceite
Código executando sem erros e layout sem estouros de tela (overflow).
