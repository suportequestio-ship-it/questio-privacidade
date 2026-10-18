# Política de Privacidade — Questio

**Vigência desta versão:** 18 de outubro de 2026
**Responsável pela extensão:** desenvolvedor independente da Questio (contato abaixo)
**Contato sobre privacidade:** suportequestio@gmail.com
**Versão da extensão a que se refere:** 2.24.7 (beta)

## 1. O que é a Questio
A Questio é uma extensão independente para navegadores Chrome (e, futuramente, Edge) que ajuda a resolver questões no site Tec Concursos (tecconcursos.com.br), com atalhos de teclado e mouse, painel de metas e estatísticas, barra de desenho e anotações, e temas. Não é afiliada, patrocinada ou endossada pelo Tec Concursos.

## 2. Resumo
- A extensão **não possui servidor próprio** e seu código **não faz requisições de rede próprias**: nada do que ela guarda é enviado ao desenvolvedor ou a terceiros pela extensão.
- Ela **lê** o conteúdo das páginas do Tec Concursos e **observa respostas de rede** dessas páginas (seção 4) para funcionar.
- Dados de uso ficam **no seu navegador**. Apenas as **configurações** podem ser sincronizadas pelo **próprio navegador** com a sua conta (seção 5).
- Não há anúncios, análise de uso (analytics) nem venda de dados.

## 3. Dados armazenados no seu navegador
A extensão só atua em páginas de `tecconcursos.com.br` (e subdomínios, via https).

**Armazenamento local** (`chrome.storage.local`; **não** sincronizado pela extensão):

| Dado | Conteúdo | Finalidade |
|---|---|---|
| Histórico de respostas | número da questão no Tec, se foi acerto ou erro (ou apenas visitada), matéria, assunto (lidos de rótulos da página), data e hora | contador, metas, estatísticas e mensagem de conclusão |
| Matérias e metas | nome da matéria, meta de questões, marca de "zerar" | metas e estatísticas por matéria |
| Cronômetro | tempo acumulado e marcadores de início | tempo exibido |
| Interface | tema, cores, posição/tamanho/borda das barras, meta padrão, matéria fixada, estado aberto/fechado | lembrar como você usa a extensão |
| Barra de desenho | apenas **configurações**: cores, espessuras, forma, posição | lembrar preferências |
| Alternativas riscadas | quais alternativas (posições) você riscou, por questão, identificada por um código (hash) calculado a partir do conteúdo da página; guarda as 800 mais recentes | lembrar riscos ao voltar à questão |
| Marcador temporário de exclusão | identificador e hora, existente só durante "Apagar todos os dados" | coordenar a exclusão entre abas |

**Armazenamento de sincronização** (`chrome.storage.sync`): atalhos de teclado, mouse e controle, perfis, **ações personalizadas** e seletores/textos que **você** digitar, tema, cores do desenho e preferências. **Não digite dados pessoais nesses campos.**

**Não são gravados:** seus **traços e textos desenhados** na página (ficam só na memória da aba e somem ao fechá-la ou recarregá-la), o texto do enunciado e das alternativas, senhas, e-mail, cookies ou dados de cadastro. A extensão não lê campos de login ou cadastro.

O histórico de respostas é atividade de estudo associada a este navegador e perfil; trate-o como dado pessoal seu.

## 4. Como a extensão trata informações do Tec Concursos
1. **Leitura da página.** Para identificar a questão, as alternativas, a matéria e o assunto e executar o que você pede (clicar, riscar, desenhar), a extensão lê o conteúdo da página no seu navegador. Textos de enunciado e alternativas **não são guardados**; matéria, assunto e número da questão **são** guardados conforme a seção 3.
2. **Observação de respostas de rede.** Para saber se você acertou ou errou, a extensão intercepta as funções de requisição (`fetch` e `XMLHttpRequest`) da página. **Somente nos 20 segundos seguintes a uma ação sua de responder** (clique, tecla ou botão da extensão), ela lê o corpo de respostas de requisições **ao próprio site do Tec Concursos** (domínio `tecconcursos.com.br` e subdomínios) do tipo POST/PUT/PATCH, ou cujo endereço contenha termos como "resposta", "gabarito" ou "resultado". Ficam de fora: requisições a outros domínios (inclusive serviços de análise e anúncios), endereços com nomes típicos de telemetria (como "analytics", "telemetry", "beacon", "logs"), respostas que não sejam texto/JSON (imagens, HTML, binários) e corpos acima de 150.000 caracteres. Como a extensão ainda não conhece o endereço exato que o Tec usa para o resultado, outras requisições do próprio Tec feitas nesses 20 segundos podem ser lidas. A leitura é **em memória**, procurando indicação de acerto/erro. **O corpo da resposta não é salvo nem transmitido pela extensão.**
3. **O que sobra dessa leitura.** Apenas um aviso interno com: caminho do endereço (sem parâmetros), método, status, indicação de acerto/erro (se encontrada) e até 15 nomes de campos do nível superior da resposta. Os últimos 15 avisos ficam **na memória da aba** (para o Diagnóstico) e são descartados ao trocar de questão ou fechar a aba. Se houver indicação de acerto/erro, ela vira o resultado registrado no histórico (seção 3).
4. **Visibilidade para outros scripts.** Esse aviso interno é emitido na própria página; **scripts da página ou de outras extensões podem, em tese, observá-lo**. Ele não contém o corpo da resposta, o histórico nem anotações.
5. **Ações no Tec.** Cliques e teclas executados pela extensão são recebidos pelo Tec como se fossem seus.
6. A extensão **não acessa** o Tec fora do navegador, não faz login por você e não coleta suas credenciais.
7. **Aviso na primeira utilização.** Ao abrir uma página do Tec pela primeira vez, a extensão exibe um aviso resumindo esta seção e a seção 3. Você escolhe "Entendi e continuar" (a escolha fica guardada no armazenamento local) ou "Desativar a Questio". O aviso volta a aparecer depois de "Apagar todos os dados".

## 5. Sincronização pelo navegador
Somente `chrome.storage.sync` (configurações, não histórico) pode ser sincronizado, **e apenas pelo Chrome ou Edge**, se você ativou a sincronização do navegador. Isso segue a política do navegador e da sua conta Google/Microsoft; a Questio não controla nem recebe esses dados. O histórico, as matérias, os tempos, a aparência e os riscos ficam no armazenamento local e não são sincronizados pela extensão.

## 6. Compartilhamento e serviços de terceiros
O botão **Apoiar** abre, em uma nova aba, a página da Questio no **LivePix** (`https://livepix.gg/questio`), serviço de terceiros com política própria. A extensão não envia nenhum dado seu ao LivePix; qualquer pagamento ocorre no site dele, fora da extensão.

Não há compartilhamento, venda ou transferência de dados a terceiros pela extensão. A extensão não usa serviços externos, SDKs, analytics, anúncios nem código remoto. Possíveis tratamentos pelo Tec Concursos (ao receber suas ações) e pelo seu navegador (sincronização) seguem as políticas deles.

## 7. Permissões solicitadas
- **`storage`**: guardar os dados e configurações descritos na seção 3.
- **Acesso a `tecconcursos.com.br` e subdomínios (https)**, concedido por script de conteúdo: ler a página, exibir as barras e painéis, acionar a página e observar respostas (seção 4). A extensão não pede acesso a outros sites nem permissões de histórico, abas, cookies ou rede.

## 8. Por quanto tempo guardamos
- **Histórico de respostas:** entradas com mais de 120 dias deixam de ser usadas e são descartadas quando a página do Tec é carregada. A remoção do armazenamento ocorre na próxima gravação do histórico; até lá o dado antigo pode permanecer no armazenamento do navegador, sem ser usado pela extensão.
- **Riscos:** as 800 questões mais recentes.
- **Demais dados:** até você apagá-los. Ao desinstalar a extensão, o tratamento dos dados guardados por ela segue o navegador; para ter certeza de que nada ficou, use **Apagar todos os dados** (seção 9) antes de desinstalar.

## 9. Como consultar e apagar seus dados
- **Consultar:** o painel mostra contadores e estatísticas por matéria. A extensão **não oferece** tela de listagem nem exportação do histórico bruto.
- **Zerar** (painel de progresso): apaga histórico, matérias e tempos, e desafixa a matéria. **Mantém** aparência, a meta como padrão, barra de desenho, riscos e configurações.
- **Apagar todos os dados** (Opções › aba **Aparência** › Privacidade): pede confirmação e apaga o armazenamento local e o de sincronização da extensão (histórico, matérias, metas, tempos, riscos, aparência, desenho, atalhos, perfis, ações personalizadas), confere se nada restou e informa o resultado; **não exporta nada e não pode ser desfeito**. Limites: outro dispositivo sincronizado com configuração antiga pode enviá-la de volta (apague também nele); se você fechar a página durante a exclusão ou houver falha, a tela avisa que não foi integral e você deve repetir.
- **Restaurar** (Opções): volta atalhos ao padrão. **Redefinir** (barra de desenho): volta as preferências do desenho.
- **Desinstalar** a extensão.

## 10. Diagnóstico
Se você abrir o Diagnóstico, a extensão monta um texto técnico com: versão, endereço da página (domínio e caminho, que pode conter identificadores), estrutura da barra do Tec, **os 14 primeiros caracteres** de cada alternativa e informações de estilo, a matéria detectada, contadores da matéria, os últimos avisos de rede (seção 4, item 3) e até alguns trechos curtos de texto da página com palavras de resultado ou rótulos de matéria. Não inclui o enunciado completo, o histórico, o corpo das respostas, e-mail ou cookies. **Nada é enviado automaticamente**: o texto só vai para a área de transferência quando você clica em Copiar, e o destino é decisão sua — revise antes de compartilhar.

## 11. Segurança
A extensão não carrega código remoto, não usa bibliotecas de terceiros e pede somente a permissão `storage` e acesso ao Tec Concursos. Os dados ficam no armazenamento da extensão no seu navegador, protegido pelo isolamento do próprio navegador; quem tiver acesso ao seu perfil do navegador pode acessá-los. Nenhum sistema é totalmente livre de riscos.

## 12. Crianças
A Questio é destinada a pessoas maiores de 18 anos (estudantes e candidatos a concursos) e não é direcionada a crianças. A extensão não tem cadastro, não pede idade e não envia dados ao desenvolvedor; ainda assim, se você é responsável por uma criança que usa a extensão, use **Apagar todos os dados** (seção 9) ou entre em contato pelo e-mail da seção 14.

## 13. Mudanças nesta política
Mudanças serão publicadas neste endereço com nova data de vigência. Se a extensão passar a enviar dados a algum servidor, esta política será atualizada **antes** da mudança. Mudanças relevantes na forma de tratar dados serão indicadas também nas notas da versão da extensão na loja em que ela estiver publicada.

## 14. Contato e pedidos sobre seus dados
Dúvidas ou pedidos: suportequestio@gmail.com. Como os dados ficam no seu navegador e o desenvolvedor não os recebe, você pode exercer o controle diretamente pelas opções da seção 9.

## 15. Uso limitado de dados (Chrome Web Store)
O uso das informações obtidas das páginas do Tec Concursos limita-se a fornecer e melhorar as funções descritas acima (contador, metas, estatísticas, atalhos, desenho e anotações). Os dados não são vendidos, transferidos a terceiros, usados para publicidade personalizada ou para avaliar crédito.
O uso que a Questio faz das informações recebidas está em conformidade com a Política de Dados do Usuário do Chrome Web Store, incluindo os requisitos de Uso Limitado.

*"Tec Concursos" pertence ao seu titular e é citado apenas para indicar compatibilidade.*
