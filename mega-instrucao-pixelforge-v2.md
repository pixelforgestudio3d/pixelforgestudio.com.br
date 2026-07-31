# PixelForge Studio — Mega Instrução V2 (site pixelforgestudio.com.br)

Documento único de direção para handoff ao Claude Code. Nenhum código deve ser escrito a partir desta conversa — só aqui se refina a direção completa; a implementação acontece à parte. Este arquivo é vivo: será atualizado conforme mais decisões forem fechadas. Última atualização: 31/07/2026.

**Pasta do site (repo):** `C:\Users\User\Documents\GitHub\pixelforgestudio.com.br` — todos os caminhos relativos citados neste documento (`assets/...`, `index.html`, `projects/...`, `servicos/...`) são relativos a essa pasta. Este arquivo também vive dentro dela.

---

## 0. Contexto e motivação

Ericson está reposicionando o site pra refletir o trabalho que faz hoje: direção de arte composta com motion, design gráfico, composição com IA + CGI, SKU publicitário feito só com IA, e FOOH. O site atual (commit "new site 2.0") foi construído em cima de um posicionamento 100% CGI/3D artesanal — hero e CTA dizem coisas como "campanhas visuais que nenhuma IA consegue replicar". Isso precisa ser reconciliado, não just somar conteúdo novo por cima.

**Status/urgência (31/07/2026):** Ericson quer começar a codar em breve (execução própria, direto no Claude Code) porque espera um aumento de acessos ao site em breve. Prioridade prática: fechar essa mega instrução com o que já está maduro em vez de continuar abrindo pesquisa nova indefinidamente — pesquisa de referências de estúdio (Lusion e as demais, seção 9.1.x) já foi encerrada por decisão dele nessa data.

**Posicionamento fechado:** CGI continua carro-chefe. Direção de arte é o diferencial mais forte. IA entra como ferramenta que expande possibilidades criativas e acelera o workflow — nunca como substituto do craft, e nunca desvalorizada. Reescrever hero/CTA a partir dessa lógica (hoje: "nenhuma IA consegue replicar" — precisa suavizar, não apagar o orgulho do craft CGI).

**Regras de copy — válidas pra revisão de TODO o conteúdo do site (23/07/2026):**
1. IA é inevitável no mercado — a abordagem trata IA sempre como **ferramenta**, nunca como produto final em si. Aplica pra toda menção de IA no site (hero, IA+CGI, página de serviço "CGI + AI", A Forja, etc.).
2. Evitar travar a copy em segmento de mercado (ex: "luxo") — as marcas atendidas não são todas de um nicho só. Foco em mostrar a solução/resultado, não rotular o tipo de cliente.
3. **Travessão (—) proibido no MEIO de texto corrido (parágrafos, subtítulos, descrições).** Correção do Ericson (23/07/2026): em título/headline não tem problema, pode manter. Regra vale só pra corpo de texto. Usar ponto, vírgula ou dois-pontos no lugar quando for corpo de texto.

## 1. Arquitetura do site

Site multi-página (vanilla HTML/CSS/JS, GitHub Pages, sem framework, sem build step) — decisão confirmada por Ericson especificamente pra manter cada página limpa em vez de sobrecarregar um scroll único.

**Nav (atualizado 23/07/2026):** Serviços · Projetos · FOOH · IA + CGI · A Forja · Contato

**Decisão de escopo (23/07/2026):** Projetos (cases individuais), Contato e Serviços (ver seção 5.6, 6 páginas em `servicos/`) viram página própria. FOOH, IA+CGI, A Forja e o preview de Serviços continuam como seções dentro da Home (nav com âncora, não link pra outra página) — é o padrão real da Tendril e evita fatiar demais o site.

**Ordem das seções da Home — FECHADA 23/07/2026 (Serviços com posição sugerida, a confirmar):** Hero → **Peça 3D interativa (nova, ver seção 3.1)** → Marquee → Serviços (preview) → Grid de projetos → Clientes/Escopo → A Forja → FOOH → IA+CGI → CTA final.

**Sitemap final:**
- `index.html` — Home: hero → marquee + Clientes/Escopo → grid de projetos (linka pra páginas individuais) → seção FOOH → seção IA+CGI → seção A Forja → CTA de contato
- `contato.html` — página de contato dedicada (Formspree)
- `projects/[cliente]/[projeto].html` — página dedicada por case real, modelo Tendril (capa → intro c/ ficha técnica → embed Vimeo → grid de stills → CTA → nav prev/next entre projetos → footer).

**Lista de cases com página própria — ATUALIZADA 23/07/2026 (ainda não fechada, Ericson vai definir mais um item):**
  1. Marine Fishing — Vara Legacy
  2. Marine Fishing — Carretilha Avenger
  3. Marine Fishing — Garateia Sanken 3x *(publicado no Vimeo/Behance segundo o doc master, não estava no grid atual do site)*
  4. Marine Fishing — Alicate (Big Game Pliers)
  5. Kopenhagen — Chocolate ASMR
  6. Everlast — Powerlock OG
  7. Piccadilly — Soft Step
  8. Smirnoff — Gashapon Ice Reveal
  9. Heineken — Sam's Club 0.0 DOOH
  10. Dolce & Gabbana "The One" — projeto pessoal, mas ainda ganha página própria completa (diferente do tratamento "Estudo" de Manscaped/AFPM)
  11. *(mais um, Ericson ainda vai definir)*

**Confirmado 23/07/2026:** Juvia Skincare e Cacau Show saem do plano inicial de página própria (a lista acima é a definitiva pra essa primeira leva). Ericson sinalizou que o line-up de projetos deve rotacionar no futuro — essa lista de 10-11 é o ponto de partida, não fixo pra sempre.

**Itens "Estudo" (Manscaped, AFPM) — tratamento novo, substitui a ideia de lightbox:** em vez de página ou modal, essas imagens entram DENTRO da seção "A Forja" (perfil do Ericson) como uma galeria com scroll pinado — a tela trava durante o scroll daquele trecho e vai trocando entre pelo menos 4 imagens de estudo conforme o usuário continua rolando, só then libera o scroll normal. Padrão clássico de GSAP ScrollTrigger (`pin: true` + troca de imagem por progresso do scroll, tipo página de produto Apple). Não tem ficha técnica de cliente nem estrutura de case — é parte do storytelling pessoal do Ericson, não do grid de projetos.

**Dal Cotone — papel no site (decisão importante):** NÃO vira case study nomeado com narrativa de cliente (contrato ainda no mês 1, sem resultados pra reportar, identidade da linha masculina ainda em desenvolvimento com a Rosanne). Entra como exemplo de portfólio dentro da seção "IA + CGI", ilustrando a técnica (CGI produto + composição com IA + direção de arte), sem virar case nomeado com storytelling de cliente. Assets reais já localizados em `D:\jobs\Clientes\Dal Cotone` (não precisa pedir de novo pro Ericson) — destaque pras imagens "HUMANIZADA" (frasco CGI compositado com modelo/cenário gerado por IA).

## 2. Referências de estúdio

- **Tendril** ([tendril.studio](https://tendril.studio)) — referência máxima de estúdio. Grid de cases em vídeo na home, cada um linkando pra página própria com a anatomia descrita acima.
- **Altrn Studio** ([altrn.studio](https://www.altrn.studio)) — estúdio de amigos do Ericson, CGI/motion. Referência de tipografia bold e composição de hero (wordmark gigante, vídeo pequeno centralizado, nav minimalista, muito espaço negativo). Paleta clara (creme + vermelho) NÃO se aplica — PixelForge é site escuro por identidade. Vale só a confiança tipográfica/composição.
- **Valkiria** ([valkiriaic.com.br](https://www.valkiriaic.com.br)) — referência da seção "Clientes/Escopo" (ver seção 4).
- **Ferramenta PixelForge** (Behance, [behance.net/gallery/203323851](https://www.behance.net/gallery/203323851/Ferramenta-PixelForge)) — asset próprio: render 3D da marreta nórdica (mesmo motivo do isotipo e do cursor), duas variações de material (lava vermelha/preta, cristal roxo). Reservado pra uso em detalhes Three.js (ver seção 6).

## 3. Home — Hero

**Estrutura:** vídeo abre preenchendo a tela inteira, sem headline cobrindo por cima. Ao rolar, o texto (headline + subtítulo) é revelado — por cima ou logo abaixo do vídeo. Toda a animação de entrada precisa ser refeita de forma mais dinâmica que o reveal simples atual (fade + translateY) — bom caso de uso pra GSAP ScrollTrigger + SplitText no headline.

**Copy do hero — FECHADA 23/07/2026:**
- Eyebrow: mantém "CGI · Direção Criativa · FOOH" (curto de propósito — os pilares novos como IA+CGI e Motion ganham vitrine própria na seção Serviços, não precisam caber aqui)
- H1: mantém "Imagens que não são reais — mas poderiam." (travessão em título não é problema, regra da seção 0 é só pra corpo de texto; segura bem mesmo com o reposicionamento, não é anti-IA)
- Subtítulo: **novo texto** — "Direção de arte, CGI e composição com IA para lançamentos de alto nível. Product reveals, campanhas e Fake Out of Home." (substitui o antigo, que tinha "luxo" na lista — palavra removida por ser limitante, nem toda marca atendida é definida como luxo; foco em mostrar a solução, não o segmento de mercado)
- **Stats removidos do hero** (60+ marcas, +20M views, 8+ anos design, 5+ anos CGI) — "nenhum estúdio mostra isso, isso fica pro currículo quando precisar." Bate com a decisão V2 antiga do próprio Ericson ("stats removidos da hero, logos são a prova real"), reforçada agora pela seção Clientes/Escopo.

**Asset:** Ericson já colocou o vídeo final em `assets/HERO SITE V4.mp4` (existe junto do antigo `HERO SITE V3.mp4` no repo — trocar a referência quando for pro código).

**Descartado:** a ideia original de bigorna/marreta como reveal do hero (scroll-driven, marreta bate e revela a cena) foi abandonada — Three.js fica só pra detalhes menores, não pro hero.

**Ajuste técnico 23/07/2026 (marquee):** remover o `filter: brightness(0) invert(1)` aplicado nos logos — as imagens já são brancas na origem, esse filtro é redundante/desnecessário. Manter só os estados de opacidade (0.6 padrão, 1.0 no hover).

## 3.1 Home — Peça 3D interativa (NOVA, 31/07/2026)

**Decisão do Ericson:** logo abaixo do Hero entra um "quadro" interativo em Three.js, inspirado diretamente na interação do hero do Lusion (lusion.co) — ver seção 9.1.1 pra referência completa.

**Como funciona a referência (Lusion), descrita pelo próprio Ericson depois de testar ao vivo:** não é só um objeto girando. Existe uma leve força gravitacional/atratora que puxa as peças (formas tipo cruz/pino) pro centro, mantendo elas agrupadas num aglomerado. Ao passar o mouse por cima, as peças próximas ao cursor se afastam do centro, como se o atrator fosse temporariamente desligado naquela área. Solta o mouse, a gravidade volta a puxar tudo de volta pro centro. Efeito físico, não animação de rotação simples.

**Aplicação no PixelForge:** ainda em aberto qual geometria/asset usar.
- Candidato natural: reaproveitar o asset "Ferramenta PixelForge" (marreta 3D, seção 2) já reservado — mas ele também está reservado pra dentro da seção "A Forja" (seção 5.4). **Precisa confirmar com o Ericson se é o mesmo asset em dois lugares, um asset novo só pra esse quadro do hero, ou se essa peça abaixo do hero SUBSTITUI o uso da marreta na A Forja.**
- Alternativa: peça abstrata nova (não precisa ser a marreta), só replicando o comportamento físico (atrator central + repulsão no hover) como assinatura de interação do site.

**Prioridade de implementação:** Ericson quer começar a codar em breve (ver seção 0, status/urgência) — esse é um candidato forte pra primeira leva de Three.js do site, junto com a decisão pendente da seção 6.

**Asset — FECHADO 31/07/2026:** Ericson exportou e já colocou no repo, em `assets/3D/`:
- `Isotipo_PixelForge.glb` (535 KB, versão completa)
- `Isotipo_PixelForge_otm.glb` (114 KB, versão otimizada) — **esta é a que deve ser usada no site**, confirmado pelo Ericson ("este com o final _otm é o ideal pra usar no site").

Não é a marreta nórdica do Behance ("Ferramenta PixelForge", seção 2) — é o **isotipo** do PixelForge em 3D, um modelo próprio separado. Isso resolve a pendência da seção 6/10 sobre reaproveitar ou não o asset da marreta: **não reaproveita**, é um asset dedicado só pra essa peça interativa abaixo do Hero. O uso da marreta na seção "A Forja" (seção 5.4) continua uma decisão separada, ainda em aberto.

## 4. Home — Marquee + nova seção "Clientes / Escopo"

**⚠️ Correção 31/07/2026:** a descrição de mecânica de hover abaixo (coluna paralela com tags "acendendo") estava imprecisa — a mecânica exata, revisitada e confirmada ao vivo no site de referência, está na **seção 11.4**. Usar a 11.4 como fonte da verdade pra implementação; o resto desta seção (classificação de marca→escopo, decisão de manter marquee + seção nova) continua válido.

**Decisão:** manter os dois. O marquee de logos continua rodando em loop (só um pouco maior que hoje). Entra também uma seção nova, "Clientes / Escopo", adicional — não substitui o marquee.

**Referência (Valkiria):** duas colunas alinhadas à direita — "Clientes" (nomes em texto puro, cinza apagado, sem logo visível) e "Escopo" (tags em paralelo, também apagadas). No hover de um cliente: o nome vira branco/bold, um logo pequeno aparece flutuando no espaço vazio à esquerda da lista, e na coluna Escopo só as tags daquele cliente acendem em branco (resto continua apagado).

**Vocabulário de Escopo:** texto livre por marca, não um sistema fixo de categorias — Ericson usou termos variados (CGI, Direção de Arte, FOOH, DOOH, Motion, Visualizador 3D, PackShot, Launch Film, CGI + Pós-produção) e às vezes empilha vários por marca, no mesmo espírito da Valkiria que empilha Marca/Estratégia/Produto/Embalagem.

**Classificação completa — 25/25 marcas (marca → escopo, tags empilhadas quando aplicável):**

| Marca | Escopo |
|---|---|
| Heineken | DOOH |
| Natura | CGI + Pós-produção |
| Smirnoff | CGI, Launch Film |
| Vivo | CGI |
| Everlast | CGI, Launch Film |
| Fila | CGI |
| Piccadilly | CGI, Launch Film |
| Bio Extratus | FOOH |
| Bruna Tavares | FOOH e CGI |
| Scania | FOOH |
| Caixa | FOOH |
| Osklen | Visualizador 3D |
| Decathlon | Visualizador 3D |
| TV Globo | FOOH |
| SESC | FOOH |
| Marine Fishing | CGI, Direção de Arte, Launch Film |
| Lupo | CGI e FOOH |
| Merrachi | FOOH |
| Hello Kitty | FOOH |
| Ellus | Visualizador 3D |
| AAT | Visualizador 3D e PackShot |
| Bis Sigma | FOOH |
| Lobits | FOOH |
| Positivo | CGI |
| Rodonaves | Visualizador 3D (VR Unreal) |

## 5. Home — Grid de projetos: atualização de links

| Card atual | Ação | Link novo |
|---|---|---|
| Vara Legacy (Marine Fishing) | Atualizar | https://www.behance.net/gallery/244804945/Marine-Fishing-Legacy-3D-Product-Film |
| Kopenhagen (Chocolate ASMR) | Atualizar | https://www.behance.net/gallery/251880485/Kop-Week-2024-Kopenhagen |
| Powerlock OG (Everlast) | Atualizar | https://www.behance.net/gallery/250176779/Everlast-Powerlock-3D-Product-Showcase |
| Smirnoff (Gashapon Ice Reveal) | Atualizar | https://www.instagram.com/reel/DM_N6Nbxr7I/ |
| Heineken (Sam's Club 0.0, DOOH) | Manter link atual | — |
| Piccadilly (Soft Step) | Manter link atual | — |
| Carretilha Avenger (Marine Fishing) | Atualizar | https://www.behance.net/gallery/240175183/Marine-Fishing-Avenger-Launch-Film |

Lista parcial — Ericson ainda vai mandar mais atualizações de link.

## 5.1 Home — Grid de projetos (ajuste de escopo)

O grid da Home passa a ser vitrine/preview que linka pra `projects/[cliente]/[projeto].html` (seção 1) em vez de abrir Behance/Instagram direto. A tabela de links da seção 5 fica valendo como referência de origem/fonte de cada case (usar nas páginas de projeto — embed, créditos, link "ver no Behance"), não necessariamente como link direto do card na Home.

**Legenda "Vara Legacy — Launch Film":** mantém o travessão, é label/título de card, não corpo de texto (regra da seção 0 corrigida, travessão só é proibido em texto corrido).

**Interação do card, NOVA 23/07/2026 (referência basement.studio, ver seção 9.1.2):** thumb sem texto por padrão. Hover dispara o vídeo de preview tocando e revela o nome do projeto. O card inteiro é clicável e leva pra página do projeto, substitui o padrão atual de botão pequeno no canto (`.pa`, seta no canto superior direito) que o Ericson achou fora de fluxo de UI.

## 5.2 Home — Seção FOOH

Mantém a estrutura atual (carrossel 3D dos 12 vídeos FOOH + texto aprovado já existente: "O impossível na rua."). Ainda não redesenhado a fundo nessa rodada — ajustes de animação (GSAP) entram no passe global (seção 6). Sem mudança de conteúdo/curadoria decidida ainda.

**Fix de estilo (23/07/2026):** subtítulo atual "Instalações que param o scroll — e o trânsito." tem travessão, trocar por "Instalações que param o scroll e o trânsito." Resto do texto do FOOH já está ok (sem travessão, sem menção a IA ou luxo).

## 5.3 Home — Seção "IA + CGI" (nova)

**Correção importante do Ericson (23/07/2026) sobre a v1 do rascunho:** a divisão "CGI = produto, IA = cenário" foi rejeitada. Soa como recortar uma foto do produto e colar dentro de uma imagem gerada por IA, o que não é real. O processo de verdade: CGI gera uma parte, IA gera outra parte, e a composição dos dois forma uma peça única. IA não fica travada só em "cenário". Aplicar esse cuidado em qualquer texto futuro que descreva IA+CGI no site (inclusive o card de Serviços da seção 5.6, que já evita essa armadilha ao falar em "camadas" ao invés de produto/cenário).

**Regra nova:** essa seção não cita nome de marca nenhum em texto. A seção Clientes/Escopo já cobre marca + o que foi feito, não precisa repetir aqui.

**Copy FECHADA 23/07/2026 (funciona tanto pra imagem quanto vídeo, confirmado pelo Ericson):**
- Label: "05 — IA + CGI"
- Título: "Controle e velocidade, numa imagem só."
- Corpo: "CGI e IA não competem, se compõem. Cada tecnologia entra numa camada diferente do processo (modelagem, textura, luz, ambientação) até a composição final fundir tudo numa peça só, pronta pra publicar."

Conteúdo principal: Dal Cotone (Fresh Skin, Luxy, Provoke, Sweet Crush + versões HUMANIZADA, usando os renders mais recentes de `assets/NOVAS IMAGENS/`, ver seção 9) — trabalho real de cliente, sem virar case nomeado com narrativa (motivo já registrado na seção 0). Onde exatamente os itens "Estudo" (Manscaped, AFPM) encaixam — só na galeria da A Forja (seção 5.4), também aqui, ou dividido — **fica em aberto por decisão visual do Ericson**, ele quer ver o layout desenhado antes de decidir onde cada imagem entra melhor. Não presumir.

## 5.4 Home — Seção "A Forja"

**Estrutura FECHADA 23/07/2026:** posição logo depois de Clientes/Escopo (ver seção 1). Duas camadas, não três — a "galeria pinada" absorve a foto de perfil como primeiro frame, resolvendo o problema de layout de layers competindo:
1. **Texto de missão/bio já aprovado** (existe no doc master do Ericson, título "Feito à mão. Renderizado na alma.") — reaproveitar como base, não reescrever do zero.
2. **Galeria com scroll pinado** — começa com a foto real do Ericson (`assets/perfil/FOTO PRINCIPAL VF.png`) e vai trocando, conforme o usuário rola, pros renders "Estudo" (Manscaped/AFPM, pelo menos 4 imagens) — narrativa visual "a pessoa → o que ela cria". GSAP ScrollTrigger `pin: true`, troca de imagem por progresso do scroll.

**Copy da bio, FECHADA 23/07/2026:** reescrita em primeira pessoa do plural (mesmo sendo o Ericson sozinho hoje, "passa mais credibilidade"), tirou menção a técnicas específicas do Houdini (RBD/FLIP, deixa em aberto pra qualquer simulação), trocou "direção de arte para publicidade high-ticket" por "publicidade global":
- P1: "Na PixelForge, a premissa é literal: forjar cada pixel até atingir a singularidade. Lideramos um processo onde a direção de arte soberana guia a tecnologia, e não o contrário."
- P2: "Nosso arsenal inclui Cinema 4D com Octane Render e simulações físicas reais no Houdini. Controle absoluto sobre cada detalhe, do primeiro frame ao render final. A IA entra quando acelera esse processo, nunca no lugar dele."
- P3: "Nossa expertise na publicidade global garante que a complexidade técnica esteja sempre a serviço de uma narrativa visual impecável e estratégica."

**Peça 3D em Three.js (marreta) — EM ABERTO POR DECISÃO DELIBERADA (31/07/2026):** ainda reservada pra essa seção (ver seção 6), mas o encaixe exato ainda não foi desenhado — Ericson quer pensar melhor, acha que pode acabar sendo bem mais simples do que o que vinha sendo discutido. **Não é bloqueio pro início da implementação** — pode entrar como fase posterior da seção "A Forja" (texto + galeria pinada primeiro, marreta depois quando ele decidir o formato). Claude Code não deve propor solução aqui, só deixar o espaço reservado até o Ericson confirmar.

**Banner/cabeçalho da seção, NOVO 23/07/2026:** entrada da seção A Forja ganha uma tarja/banner de imagem: `assets/NOVAS IMAGENS/Frame_Marreta_PixelForge3.png` (cortada, não precisa aparecer inteira, corte pra não ficar grande demais), com um fade leve por cima e o título "A FORJA" sobreposto. Outros assets de marreta disponíveis na mesma pasta pra variações futuras: `Beauty_Marreta.png`, `Capa Marreta.png`, `GIF_Marreta.gif`. **Em aberto:** esse banner substitui a peça interativa em Three.js, ou os dois convivem (banner estático de entrada + elemento 3D interativo em outro ponto da seção)? Confirmar com o Ericson.

**Galeria pinada, posição confirmada:** entra DEPOIS do efeito de pin scroll (a sequência foto → renders já descrita acima). Um botão aparece embaixo das imagens assim que elas terminam de aparecer. **Em aberto:** o que esse botão faz/pra onde leva (expandir, abrir lightbox, ir pra outra página tipo a galeria de projetos pessoais mencionada na seção 9.1) — confirmar com o Ericson.

## 5.5 Home — CTA final / teaser de Contato

Mantém o H2 atual ("Pronto para forjar o impossível?"). Botão agora deve linkar pra `contato.html` (página dedicada com Formspree) em vez de abrir WhatsApp direto. WhatsApp continua existindo, só que dentro da página de contato, não como único canal do CTA principal da Home (decisão já registrada no doc master do Ericson: Formspree é o formulário principal, WhatsApp fica mais discreto).

**Subtítulo do CTA, FECHADO 23/07/2026:** "Vamos criar campanhas visuais impossíveis de ignorar. Direção de arte e tecnologia trabalhando a ideia até o resultado perfeito!" (substitui "Vamos criar campanhas visuais que nenhuma IA consegue replicar. Craft real. Resultado impossível de ignorar." Corrigida concordância "impossível" → "impossíveis" para combinar com "campanhas".)

## 5.6 Serviços — estrutura nova (23/07/2026)

Ideia nova do Ericson: uma citação/preview compacta de cada serviço em algum lugar da Home (ou página própria de listagem — "talvez uma página isolada"), com cada serviço linkando pra uma página dedicada.

**Serviços confirmados (6):**
1. Launch Film
2. 3D Film
3. Packshot
4. FOOH
5. CGI + AI
6. Pós-produção

**Formato do card/citação (preview):** nome do serviço, resumo curto, uma imagem ou vídeo de exemplo, CTA "Saiba mais" → leva pra página do serviço específico.

**Página de cada serviço (`servicos/[nome].html`):** explica o serviço em detalhe. Rodapé obrigatório em toda página de serviço: (1) lista dos outros 5 serviços (cross-link), (2) CTA "Propor projeto" → `contato.html`.

**Sitemap — adiciona:**
- `servicos.html` — hub com os 6 cards de preview (se vier a ser página isolada em vez de seção da Home — a confirmar exatamente onde mora essa listagem)
- `servicos/launch-film.html`
- `servicos/3d-film.html`
- `servicos/packshot.html`
- `servicos/fooh.html`
- `servicos/cgi-ai.html`
- `servicos/pos-producao.html`

**Decisões 23/07/2026:** o preview dos 6 serviços vira seção nova na Home (não fica só numa página isolada). "Serviços" entra no nav principal.

**Copy dos previews — rascunho v3, ainda em refinamento:**
1. **Launch Film** — "Filme de lançamento em CGI 3D, do conceito à entrega. Um modelo, e o material vira reel, stories, e-commerce e PDV." *(aprovado)*
2. **3D Film** — "Produção 3D sob medida pra qualquer momento de campanha, sazonal ou pontual, com direção de arte própria fora do contexto de lançamento." *(trocou "datas comemorativas" por "sazonal", tirou os exemplos entre parênteses — Ericson achou que citar Páscoa/Natal era desnecessário; termo "sazonal" ainda pode melhorar)*
3. **Packshot** — "Still de produto renderizado em CGI: luz, ângulo e material sob controle total, com variações ilimitadas a partir de um único modelo 3D." *(ângulo novo — evita repetir o motivo "impossível" que já aparece no FOOH, foca em variações ilimitadas a partir de 1 modelo, argumento que o Ericson já usa em vendas)*
4. **FOOH** — "Fake Out of Home. CGI integrado ao mundo real, instalações impossíveis que rodam a internet sem locação." *(fechado no conteúdo, só troquei o travessão por vírgula pra seguir a regra de estilo nova)*
5. **CGI + AI** — FECHADO 23/07/2026, formato de dois níveis:
   - **Card de preview na Home (curto):** "3D pra controle. IA pra velocidade. Juntos, fecham um produto final completo e profissional."
   - **Abertura da página dedicada `servicos/cgi-ai.html` (completo):** "3D garante controle: posição, câmera, ângulo, rótulo, shader base. IA acelera: gera imagem, textura e luz pra compor por cima e fechar um produto final completo e profissional."
   - *(outras variações descartadas nessa rodada: versão com "controle/velocidade" invertidos e versão narrativa longa)*
6. **Pós-produção** — "Compositing, chroma key, VFX e motion: a camada final que transforma render em imagem publicável." *(aprovado, só troquei travessão por dois-pontos)*

**Nav atualizado:** Serviços · Projetos · FOOH · IA+CGI · A Forja · Contato

**Posição sugerida na Home (a confirmar):** logo depois do Marquee, antes do Grid de projetos — lógica de "o que eu faço" antes de "aqui está a prova". Ordem completa proposta: Hero → Marquee → **Serviços** → Grid de projetos → Clientes/Escopo → A Forja → FOOH → IA+CGI → CTA final.

**Ainda em aberto:** conteúdo de cada página de serviço (`servicos/[nome].html`) ainda não escrito.

## 6. Stack de animação

- **GSAP** (ScrollTrigger + SplitText + ScrollSmoother — 100% gratuito desde abril/2025, inclui os plugins que antes eram pagos) — motor principal de scroll-storytelling em todo o site: pinning nas seções de case, reveals de texto, scroll suave, animação de entrada do hero.
- **anime.js** — coisas pequenas e leves: reconstruir o loader/isotipo (hoje é SVG+JS na mão) e micro-transições de UI, onde não vale carregar GSAP inteiro.
- **Motion (motion.dev)** — fora do escopo por enquanto. Faria o mesmo trabalho que GSAP já cobre aqui; usar os dois juntos seria redundância sem ganho.
- **Three.js** — só em detalhes pontuais, não no hero em si (o hero continua vídeo). Candidatos discutidos, ainda sem decisão final de asset/local exato:
  1. **Peça interativa logo abaixo do Hero (seção 3.1) — FECHADA 31/07/2026.** Física de atrator central + repulsão no hover, inspirada no Lusion. Asset: `assets/3D/Isotipo_PixelForge_otm.glb` (isotipo do PixelForge em 3D, versão otimizada 114 KB — usar essa, não a versão completa de 535 KB). Prioridade alta, primeira peça Three.js a implementar.
  2. Peça 3D na seção "A Forja" reaproveitando o asset "Ferramenta PixelForge" (marreta nórdica do Behance, seção 2) — asset diferente do item 1 (confirmado: o item 1 usa o isotipo, não a marreta). Encaixe exato dentro da estrutura de 2 camadas da A Forja ainda em aberto (seção 5.4).
  3. Mini-viewer 3D num case pontual reaproveitando o motor do projeto pessoal "3D Studio" do Ericson (Three.js r160, já documentado no doc master dele) — ideia de fase futura, não prioritária agora.

## 7. Ideias de diferenciação (sugeridas, ainda não aprovadas)

Levantadas como propostas pra dar identidade única ao site, além do redesign básico — Ericson ainda não confirmou quais quer:
- Indicador de progresso de scroll que "esquenta" como metal (gradiente frio→quente conforme desce a página).
- Slider de comparação Foto vs. CGI num case selecionado (arrasta e revela o render sobre a foto real) — reforça o argumento "CGI faz o que foto não consegue" que ele já usa em abordagens comerciais.
- Toggle "clay/wireframe → final" num still de destaque, mostrando o passe de render por trás do resultado final.
- Cursor customizado (já é um diferencial — marreta pixel art) evoluir pra mostrar preview em vídeo loop perto da ponta do cursor ao passar sobre card de projeto.

## 8. Roteiro de etapas — LIBERADO PRA HANDOFF (31/07/2026)

Ericson confirmou início da implementação no Claude Code a partir daqui. Esse documento inteiro é a instrução de referência; qualquer seção marcada "em aberto" deve ser tratada como pendência a confirmar com ele, não decidida por conta própria durante a implementação.

**O que já está 100% fechado e pode ser codado sem mais alinhamento:**
- Hero (seção 3): copy final, asset `HERO SITE V4.mp4`, comportamento de reveal ao scroll.
- Peça 3D interativa abaixo do Hero (seção 3.1): física atrator/repulsão, asset `assets/3D/Isotipo_PixelForge_otm.glb`.
- Marquee + Clientes/Escopo (seção 4): classificação completa das 25 marcas.
- Grid de projetos — links (seção 5) e nova interação de card (seção 5.1).
- FOOH (seção 5.2), IA+CGI (seção 5.3, copy fechada — curadoria de imagens ainda tem pendência menor), CTA final (seção 5.5).
- A Forja (seção 5.4): texto/bio fechado e galeria pinada fechada — só a peça da marreta fica de fora dessa primeira leva (ver nota na seção 5.4).
- Serviços (seção 5.6): copy dos 6 serviços fechada, estrutura de páginas definida.
- Stack de animação (seção 6): GSAP + anime.js confirmados; Three.js com prioridade clara (peça do hero primeiro).

**Ordem sugerida pra implementação (primeira leva):** Hero + peça 3D interativa → Marquee/Clientes-Escopo → Grid de projetos (com nova interação de hover) → A Forja (bio + galeria pinada, sem a marreta) → FOOH → IA+CGI → Serviços → CTA final → páginas internas (Contato, template de projeto, páginas de serviço).

**Etapas de refinamento original (ainda válidas como referência de sequência):**

1. **Home** — hero (reanimação, seção 3), marquee + Clientes/Escopo (seção 4), links de projeto (seção 5). Maior parte já fechada.
2. **Seção "IA + CGI"** — curadoria do que entra (Dal Cotone + o que mais), puxando de `assets/NOVAS IMAGENS/` (pasta nova que o Ericson está montando com imagens recentes) e de `D:\jobs\Clientes\Dal Cotone`.
3. **Template de página de projeto** (`projects/[cliente]/[projeto].html`) — estrutura de ficha técnica, ordem de blocos, modelo Tendril.
4. **"A Forja"** — texto já aprovado existe (seção do doc master), decidir se ganha algo a mais (candidato natural pro detalhe em Three.js, ver abaixo).
5. **Contato** — página dedicada, Formspree.
6. **Passe global de animação** — GSAP (ScrollTrigger/SplitText/ScrollSmoother) em todo o site, loader/isotipo refeito em anime.js.

**Recomendação pro Three.js (pendência da seção 6):** colocar a marreta 3D interativa na seção "A Forja" — é a assinatura pessoal do Ericson, baixo risco de pesar a página (é uma peça isolada, não compete com o conteúdo de case), e reaproveita o asset que já existe. Deixar o mini-viewer 3D de produto (motor do "3D Studio") como ideia pra uma fase futura, num case específico, não nessa rodada — evita empilhar duas features 3D novas ao mesmo tempo. A confirmar com o Ericson.

## 9. Banco de imagens novas (`assets/NOVAS IMAGENS/`)

Ericson populou a pasta com ~50 arquivos recentes. Catalogado por projeto, com sugestão de destino:

**MANSCAPED — spec AI+CGI, marca internacional (HERO 1/2/3, AMBIENTADA 2/3, CLOSE 2/3v2, Explodido 2, HUMANIZADA 3, WIP 32/38/45/47).** Qualidade altíssima: still de produto puro (fundo preto, respingo tipo tinta) + cenas "ambientada"/"humanizada" com composição de IA (banheiro fotorrealista). Como é marca reconhecida globalmente e não tem risco de confidencialidade de cliente (parece spec pessoal), é candidata forte a virar o exemplo-bandeira da seção "IA + CGI" — possivelmente mais forte que Dal Cotone por ser marca que todo mundo reconhece. **A confirmar com Ericson: é spec pessoal (sem restrição de uso) ou trabalho pra terceiro com alguma restrição?**

**Dal Cotone — Fresh Skin, Luxy, Provoke, Sweet Crush + versões HUMANIZADA, Teste 01 Render.** Mesma linha já mapeada em `D:\jobs\Clientes\Dal Cotone`, só que com renders mais recentes (datas 16–20/07). Usar essas versões (mais novas) na seção IA+CGI em vez das que já estavam na pasta do cliente.

**D&G "The One" — COMP STILL DG_STILL FINAL DOLCE GABANNA, SHOT FLORAL D&G.** Projeto em desenvolvimento ativo (Houdini FLIP fluids, confirmado no doc master do Ericson). Ainda sem confirmação se já pode ir pro site ou se é WIP confidencial.

**Marine Fishing — CAPA BEHANCE GARATEIAS, CAPA BEHANCE V1/V3 ALICATE, FRAME 1/2/X VARA LEGACY, CAPA VARA LEGACY.** "Alicate" = "Marine Sports Big Game Pliers", projeto publicado no Behance (citado no doc master) mas que HOJE NÃO está no grid do site — candidato a card novo. As capas/frames de Vara Legacy e Garateias são refresh de cover art pra cases que já existem no grid.

**Kopenhagen — CAPA BEHANCE KOPENHAGEN, TITULO KOPENHAGEM.** Refresh de cover pro case que já existe no grid.

**Everlast — CAPA BEHANCE EVERLAST, WIP (1) ZBRUSH EVERLAST.mp4, WIP (18)/(24) ZBRUSH EVERLAST.** Refresh de cover + material de processo/BTS, útil pra página de projeto individual (seção de process/pipeline que o doc master já definia pro case Everlast).

**Smirnoff — CAPA SMIRNOFF ICE GACHAPON.** Refresh de cover pro case que já existe no grid.

**Cacau Show — CAPA CACAU SHOW CROP.** Chocolate/gift box CGI (embalagem "LaNut Pistache" flutuando com balões). Marca nova, não está no portfólio atual — candidato a card novo.

**Juvia Skincare — JUVIA_STILL_01–04, SPEC AD JUVIA NUTSTICK FINAL.mp4.** Cliente real, spec ad publicado (marca aprovou, "ficou magnífico" segundo o doc master do Ericson) — mas não está no site hoje. Candidato a card novo.

**Olera — IMG OLERA 1.** Lead do funil de prospecção (existe `proposta-olera.html` no repo, mas não é case publicado). Provavelmente NÃO deveria ir pro portfólio ainda — é material de proposta, não trabalho fechado. A confirmar.

**AFPM — STYLE FRAME 1/2/3 V1/V2 AFPM.** Segundo o doc master do Ericson, esse projeto teve problema de pagamento (recebeu só metade do combinado, projeto principal travado). **Não presumir que deve entrar no portfólio — confirmar com Ericson se ele ainda quer mostrar esse trabalho apesar da situação com o cliente.**

**Decisões 23/07/2026:**
- **Manscaped:** sem restrição de uso — é um teste que enviaram pro Ericson por causa de uma vaga de emprego, não é trabalho pago por cliente. Vira exemplo-bandeira da seção IA+CGI, mas rotulado como **"Estudo"** — não como case de cliente. A copy/legenda precisa deixar claro que é um teste/exploração pessoal, não implicar que a Manscaped contratou o PixelForge.
- **Juvia Skincare, Cacau Show, Alicate (Marine Sports Big Game Pliers):** todos confirmados como card novo no grid principal — esses SIM são cases reais de cliente/trabalho fechado, sem o rótulo "Estudo".
- **Olera:** fica de fora (não é case fechado, é material de proposta comercial ainda em aberto).
- **AFPM:** entra, também rotulado como **"Estudo"** (mesmo tratamento do Manscaped) — não como case de portfólio fechado, já que teve pendência de pagamento com o cliente.

**Rótulo "Estudo" — padrão a definir:** vai precisar de algum indicador visual consistente pra marcar esses itens como estudo/exploração e diferenciar de case real de cliente (ex: uma tag pequena tipo "Estudo" nos cards do grid, ou um filtro na seção IA+CGI). Detalhar isso quando desenhar o grid/seção.

## 9.1 Ideia em aberto — galeria/página de projetos pessoais

Ericson está considerando uma seção ou página separada só pra projetos pessoais (candidatos naturais: D&G "The One", e possivelmente os "Estudo" também) em vez de espalhar esse conteúdo pela A Forja/IA+CGI/grid de projetos. Ainda não decidido ("ainda to pensando") — não presumir, não implementar até ele confirmar o formato.

## 9.1.1 Referência forte: Lusion (lusion.co) — pesquisa concluída 31/07/2026

Ericson ficou muito animado com essa referência (23/07/2026). Pediu explicitamente **sem som** na página (acha incômodo). Navegação ao vivo feita em 31/07/2026 (Ericson acompanhou na própria aba) cobriu Home e o início da página About; achados abaixo. Ericson deu sinal pra encerrar a pesquisa nesse ponto ("nao precisa continuar... deu pra entender o site ja e ta bem legal") — não presumir mais detalhes além do que está documentado aqui.

**Home — hero:** objeto 3D pinado (peças tipo cruz/pino) no centro da tela. **Comportamento correto (corrigido pelo Ericson depois de eu descrever errado como "girando"):** não é rotação simples — existe uma força gravitacional/atratora que mantém as peças agrupadas puxando-as pro centro; ao passar o mouse por cima, as peças próximas ao cursor se afastam, como se o atrator fosse desligado ali; solta o mouse, a gravidade volta a puxar tudo de volta. Essa é a referência exata da nova seção 3.1 (peça interativa abaixo do hero do PixelForge).

**Home — sequência de reveal:** ao rolar, headline "Bold Ideas, Brought to Life" aparece por cima/ao lado da cena 3D pinada, com uma linha em SVG azul se desenhando (path animation) conforme o scroll avança, junto de um card pequeno à direita que troca de imagem (preview de vários projetos) sincronizado com o scroll — funciona como uma "amostra" de projetos antes da seção de vídeo.

**Home — seção de showreel:** bloco grande "PLAY REEL" com vídeo de fundo em loop (mostra vários projetos em sequência rápida), não é literalmente um player que precisa de clique — o texto/botão central é mais estético que funcional nesse ponto do scroll.

**Home — "Featured Work" (grid de projetos):** cards em duas colunas, limpos, sem muito 3D. Confirma o feedback do Ericson sobre basement.studio (seção 9.1.2) de preferir design mais clean, menos 3D.

**Transição pro projeto (clique no card):** ao clicar, dispara uma transição rápida de blur + zoom (a imagem do card "avança" pra dentro da tela borrada) que termina na página de detalhe do projeto. Layout da página de projeto: título grande, texto descritivo à esquerda, colunas "SERVICES" e "LINKS" (tags de serviço + links externos tipo GitHub/Product Hunt), botão "LAUNCH PROJECT", painel de mídia grande à direita, indicador "SCROLL TO EXPLORE" no rodapé, botão "BACK" no header. **Referência direta pro template de página de projeto do PixelForge (seção 1, `projects/[cliente]/[projeto].html`)** — vale considerar o mesmo padrão de transição blur+zoom ao clicar num card da Home.

**About — hero:** abre com wordmark gigante "LUSION" sobre uma nuvem de partículas tipo explosão (provavelmente a "interação de letras" que o Ericson citou antes — não deu tempo de confirmar interação direta do mouse com as letras). Ao rolar, essa cena transiciona pra uma sequência cinematográfica pinada e MUITO longa (scroll-scrub de altíssima granularidade): um astronauta caminhando por uma cratera lunar, nuvem de partículas acima dele, texto sobreposto "WE ARE LUSION / A CREATIVE PRODUCTION STUDIO" e "CRAFTING UNIQUE DIGITAL EXPERIENCES". Pesquisa foi interrompida aqui por decisão do Ericson (não valia continuar rolando só pra ver o resto) — **as seções "Expertise" com cards e o resto do About não foram exploradas.** Não presumir conteúdo dessas partes.

## 9.1.2 Referência: basement.studio

Feedback do Ericson (23/07/2026):
- **Showcase de projetos:** thumbs sem texto por padrão. No hover do mouse, dispara animação de preview (vídeo tocando) e nome do projeto aparece. **A thumb inteira é clicável** e leva pra página do projeto, não um botãozinho pequeno no canto como o PixelForge tem hoje (`.pa`, seta no canto superior direito dos cards) — ele achou esse padrão atual "fora de fluxo". **Ação:** atualizar spec do Grid de Projetos (seção 5.1) pra esse comportamento: card inteiro clicável, hover com preview de vídeo + nome do projeto.
- **Transição entre páginas:** muito boa, tipo efeito de pixels (dissolução/glitch pixelado). Referência forte pra transição de página do site inteiro.
- **Calibração geral importante:** achou o site "3D demais" pro gosto dele. Não quer tanto 3D, prefere design mais limpo. Reforça a decisão já tomada de reservar Three.js só pra detalhes pontuais (marreta na A Forja), não usar 3D pesado em todo canto — agora com razão estética confirmada, não só técnica/performance.

## 9.1.3 Referência: Immersive Garden

Único ponto que o Ericson gostou: transição entre páginas, "bem suave e fluida, bem leve". Terceira referência de transição de página junto com basement.studio (pixel) e Lusion (ainda a explorar) — leve é a palavra-chave aqui, contrasta com algo pesado tipo o pixel dissolve do basement. A conciliar quando desenhar a transição final.

## 9.1.4 Referência: Yellow Fellow

Ericson gostou mas "não faz meu estilo" — não é referência de direção geral. Uma ideia pontual pra aproveitar: uma interação pequena com uma "bigorninha" (bigorna) em algum lugar do site, no espírito da interação que a Yellow Fellow tem no hero deles. Ideia ainda solta, não desenhada.

## 9.1.5 Referência: Microdot

Ericson achou a estética "FODA" (elogio forte), mas sem detalhe específico do que aproveitar ainda.

## 9.1.6 Lusion, referência mais forte

Confirmado pelo Ericson como a que mais impressionou de todas. Achados da navegação ao vivo consolidados na seção 9.1.1 (concluída 31/07/2026) — inclui a spec da peça interativa nova (seção 3.1) e a referência de transição pro template de projeto (seção 1).

## 9.2 Demais páginas — abordagem

Ericson quer colar perto das referências já mapeadas (seção 2: Tendril principalmente) pras páginas restantes (Contato, template de projeto, páginas de Serviços). Pra animação especificamente, pediu uma pesquisa de vários estúdios de 3D/design pra ele navegar um a um e se inspirar antes de definir a direção de cada página nova. Lista de referências entregue em chat em 23/07/2026 (ver resposta da sessão) — Ericson vai escolher o que quer aplicar depois de olhar.

## 10. Em aberto / pendências

- Peça interativa abaixo do Hero (seção 3.1) FECHADA — asset definido (`Isotipo_PixelForge_otm.glb`). Falta só decidir o encaixe da marreta dentro da A Forja (seção 5.4/6, item 2).
- Mais atualizações de link de projeto, conforme Ericson for mandando.
- Confirmar quais das ideias da seção 7 entram.
- Template completo de página de projeto individual (`projects/[cliente]/[projeto].html`) ainda não desenhado em detalhe — considerar a transição blur+zoom do Lusion (seção 9.1.1) ao clicar num card.
- Seção "IA + CGI" da home — conteúdo/curadoria além do Dal Cotone ainda não definido.
- Pesquisa de referências de estúdio encerrada por decisão do Ericson (31/07/2026) — não reabrir sem pedido explícito dele.

---

## 11. Revisão de implementação V1 — correções técnicas e de UX (31/07/2026)

Ericson revisou a primeira leva construída pelo Claude Code (rodando em modo autônomo durante a madrugada). Veredito geral: a direção de conteúdo/copy já fechada nas seções anteriores **continua valendo** — o problema não é o que foi decidido, é a EXECUÇÃO técnica e visual, que ficou muito abaixo do esperado ("site médio pra ruim", travado, sem o dinamismo das referências da seção 9.1.1). A lista abaixo é correção item a item. **Tratar como instrução de um especialista em UI/UX e Web Design** — cada item tem um motivo técnico específico do que saiu errado e o que deve substituir, dentro da direção de arte já estabelecida no resto deste documento.

**Princípio geral que faltou na V1, vale pra TODO o site:** dinamismo. A V1 ficou linear e datada — anima uma vez ao entrar em viewport e para. As referências que impressionaram o Ericson (seção 9.1.1, Lusion) têm scroll fluido, seções pinadas de verdade, e uma sensação de "convite a continuar rolando". Isso não significa 3D em tudo — significa timing, easing, pin de seção bem executado (11.1 e 11.7) e animações reversíveis (11.13), que são exatamente os pontos que saíram errados.

### 11.1 Hero — pin quebrado

**Errado na V1:** ao rolar, o vídeo do hero desaparece e o texto (headline) fica sozinho, flutuando abaixo, sem fazer sentido visual.

**Correto:** a seção do Hero fica PINADA na tela (scroll-locked) por um trecho do scroll. Durante esse trecho, o texto (eyebrow + headline + subtítulo) é revelado progressivamente SOBREPOSTO ao vídeo, que continua visível e rodando atrás o tempo todo — nunca desaparece. Só quando o texto termina de revelar 100% é que o pin libera e o scroll segue normalmente pra próxima seção (peça 3D interativa, seção 3.1). Padrão técnico: GSAP ScrollTrigger com `pin: true` na seção do hero, reveal do texto (SplitText, por linha ou palavra) amarrado ao progresso do scroll dentro desse pin (`scrub: true`), não um reveal "on enter" solto.

**Correção adicional 31/07/2026 (erro visto em nova build, print do Ericson):** o Hero está carregando já com um fade/overlay escuro por cima (gradiente no topo, imagem toda escurecida) desde o primeiro frame, antes de qualquer scroll. **Isso está errado.** O Hero tem que carregar 100% limpo — vídeo/imagem em brilho e contraste total, sem nenhum escurecimento, sem overlay nenhum. É assim que a pessoa vê o hero pela primeira vez ao entrar no site, antes de decidir rolar. O fade escuro (se necessário pra dar legibilidade ao texto) só começa a aparecer progressivamente conforme o usuário rola — amarrado ao mesmo `scrub` do pin, crescendo em conjunto com o reveal do texto, nunca antes disso. Opacidade do overlay no frame inicial = 0.

### 11.2 Peça 3D interativa (seção 3.1) — física errada, refazer — CONFIRMADO 31/07/2026

Ericson confirmou explicitamente: **física real mesmo**, do mesmo jeito que existe no hero do Lusion (seção 9.1.1) — e reforçou que lá isso é leve (baixo custo de performance), então não é desculpa pra simplificar por peso. Confirmado também: as peças (ele chama de "ícones", referindo-se ao isotipo fragmentado) devem ser **maiores** do que ficaram na V1, e **cada uma com física individual própria** (não um sistema único tratando tudo como uma massa/blob).

**Errado na V1:** o resultado foi uma bola única de mesh 3D, com as peças se sobrepondo/fundindo umas dentro das outras num aglomerado, e a única interação é afastar a bola inteira do mouse.

**Correto — física peça por peça:**
- Cada peça é um corpo independente, com física própria — elas NÃO se sobrepõem/atravessam umas as outras (precisam de colisão entre si, não só um clump visual).
- Existe uma força gravitacional leve (atrator central) que puxa todas as peças em direção ao centro, mas o resultado é um aglomerado de peças distintas se tocando/colidindo, não uma bola de mesh fundida.
- Hover: ao passar o mouse, as peças PRÓXIMAS ao cursor se afastam — cada peça reage individualmente à própria física, não a "bola" inteira se afastando como um bloco só.
- Peças podem ser um pouco maiores; a seção em si pode ser um pouco MENOR do que ficou na V1 — é só um efeito de impacto pra quem visita o site, não precisa ocupar tanto espaço de tela.
- Shader: variar entre metal/prata e vidro transparente com reflexos — não usar um material só pra todas as peças.
- Nota técnica pro Claude Code: isso é uma simulação de física real (partículas com repulsão mútua + atrator central + repulsão do mouse), não só posicionamento estático com leve rotação.
- **Investigação técnica 31/07/2026:** checamos as requisições de rede reais do lusion.co (network tab) e não há nenhuma engine de física carregada (sem WASM, sem rapier/cannon/ammo) — só os modelos 3D deles em formato próprio (`.buf`) e áudio. Forte indício de que a física de lá é um sistema custom simples calculado em JS puro a cada frame (atração ao centro + repulsão par-a-par entre peças quando ficam perto demais + repulsão do cursor), sem biblioteca externa pesada — é exatamente esse tipo de cálculo leve que resulta em algo fluido/leve. **Não usar uma lib de física completa (cannon-es, rapier, ammo.js) pra isso** — implementar o comportamento com um sistema de forças simples (Verlet ou Euler integration básica), mais leve e mais alinhado com o que a referência realmente faz.
- **Análise de vídeo 31/07/2026 (gravação enviada pelo Ericson, analisada quadro a quadro a cada 0.2s e a cada 1s):** três camadas de movimento identificadas, TODAS precisam estar presentes, não só a reação ao hover:
  1. **Animação idle contínua e independente do mouse** — mesmo sem interação nenhuma, existe uma deriva/zoom lento e constante da câmera ou do aglomerado (mudança muito gradual entre frames de 0.2s, sem nenhum salto), dando sensação de "vivo" mesmo parado. Isso precisa rodar sempre, em loop, não só quando o usuário interage.
  2. **Rotação própria de cada peça**, em eixo e velocidade levemente diferentes entre si — visível claramente comparando frames sequenciais, peças vizinhas giram de forma dessincronizada.
  3. **Respiração cíclica do aglomerado** (visível em escala de segundos, não frames) — o conjunto alterna entre um estado mais compacto e mais espalhado ao longo do tempo, sugerindo que a força do atrator central não é constante, oscila levemente (ou o raio de repulsão entre peças pulsa).
  - **Movimento em todas as camadas é extremamente suave/gradual** (sem saltos entre frames próximos) — confirma a recomendação de damping/lerp já registrada abaixo, com um fator de suavização bem baixo (movimento lento por frame).
  - **Luz:** reflexos suaves, sem sombra dura, luz parece vir de múltiplas direções (ambiente) — reforça a recomendação de HDRI/environment map abaixo.
- **Movimento (damping/lerp):** cada peça não deve pular direto pra posição alvo — persegue a posição com interpolação suave por frame (ex.: `position += (target - position) * fator_baixo`), criando o atraso/flutuação natural confirmado na análise de vídeo acima.
- **Iluminação (HDRI):** usar um environment map (HDRI) nas peças de metal/vidro em vez de luz pontual direta — dá o reflexo suave/"caro" confirmado na análise de vídeo, ao contrário de uma luz dura comum.

**Comparação direta com a implementação atual do PixelForge — análise de vídeo 31/07/2026 (gravação do Ericson, mesma técnica de frame-a-frame a cada 0.2s):**

1. **Formato das peças — CONFIRMADO 31/07/2026, não é o problema.** Ericson confirmou: o isotipo fragmentado está correto, é proposital. O problema real é só a INTERAÇÃO/física (itens 2-7 abaixo), não a geometria do asset. **Plano B, se a física não ficar boa com as peças do isotipo:** Ericson está aberto a trocar por uma geometria mais simples (ele sugeriu esferas/"bolinhas") só pra essa peça interativa, caso o isotipo fragmentado se prove difícil de fazer funcionar bem com a física de atrator+colisão+repulsão. Não é decisão fechada ainda — só uma alternativa de fallback caso a primeira tentativa com o isotipo não convença depois de corrigidos os itens 2-7.
2. **Material único, cinza/branco fosco em todas as peças** — zero variação metal/vidro, zero reflexo visível em qualquer frame analisado. Não bate com a spec.
3. **Elementos magenta/rosa não especificados:** bordas de algumas peças brilhando em magenta, e partículas rosa soltas flutuando entre as peças — não faz parte de nenhuma spec, remover (parece resíduo de outro efeito/debug).
4. **Peças se sobrepõem/atravessam visivelmente** no aglomerado — falta a colisão entre peças especificada acima.
5. **Movimento errático/instável, não suave.** Comparando frames de 0.2 em 0.2s, o aglomerado inteiro salta de posição na tela de forma abrupta (nada como a deriva lenta e controlada do Lusion), e em pontos específicos do vídeo uma peça se solta e sai voando sozinha longe do grupo sem controle — indício de simulação instável (forças descompensadas), não física contida. Precisa de amortecimento/clamping de velocidade mais forte.
6. **Peças escapando do container da seção** — em pelo menos um frame, uma peça aparece atrás do menu/header no topo da página. Precisa de um limite de posição (bounding box) que mantenha todas as peças dentro da área da seção.
7. **Ainda pequeno demais** — o pedido já registrado acima (peças maiores, seção pode ser menor) não foi aplicado.

### 11.3 Marquee "Parcerias Criativas" — fixes antigos não aplicados

Os ajustes já pedidos anteriormente (seção 3: remover filtro de brightness/invert; aumentar tamanho dos logos; adicionar nome da marca visível abaixo de cada logo) **não foram aplicados na V1** — o marquee de logos continua idêntico ao site antigo. Não é pendência nova, só não foi feita — reforçar.

**Atualização 31/07/2026:** no vídeo mais recente enviado pelo Ericson, o marquee já aparece com logo + nome da marca embaixo (Marine Fishing, Lupo, Hello Kitty, Ellus, etc.) — esse ponto específico parece ter avançado. Confirmar com o Ericson se o tamanho do logo já está adequado ou se ainda precisa aumentar mais.

### 11.4 Seção "Clientes/Escopo" — redesign completo, ficou fraca — mecânica exata verificada ao vivo no Valkiria (31/07/2026)

**Errado na V1:** a seção aparece no meio da página sem nenhum título/contexto que a apresente, o que a deixa "vaga" e nada convidativa a interagir. Distribuição visual feia. O logo (que aparece no hover) fica muito distante do nome da marca. Fonte fina demais, força a vista. O efeito de cor rosa no hover não funciona bem em cima dessa fonte fina. Animação de entrada/saída seca demais, "nada que brilhe os olhos".

**Correção geral:**
- Título/heading com mais peso visual apresentando a seção antes da lista de clientes (a label pequena "PARCERIAS CRIATIVAS" que já existe não é suficiente sozinha).
- Trocar a fonte da lista por algo mais bold/robusto — a atual é fina demais e cansa a vista, principalmente com efeito de cor por cima.
- Repensar o efeito de cor do hover (rosa) — não funcionou bem com a tipografia atual.

**Mecânica exata, confirmada revisitando valkiriaic.com.br ao vivo (Ericson pediu essa checagem específica) — isso SUBSTITUI a descrição antiga da seção 4:**
- **Não é um marquee horizontal nem uma lista estática.** É uma lista vertical comprida (as ~25 marcas, uma por linha) que rola junto com a página normal (scroll normal, a seção não fica pinada) — só que cada nome tem a opacidade controlada pela posição na tela: nomes numa faixa de foco central ficam brancos/no brilho total, nomes acima ou abaixo dessa faixa vão esmaecendo gradualmente pra um cinza apagado conforme se afastam — dá o efeito de "roleta" que o Ericson descreveu, sem precisar de máscara/fade visualmente separada, só opacidade por posição.
- **Hover:** ao passar o mouse num nome, um logo pequeno aparece flutuando no espaço vazio à ESQUERDA da lista (não fica fixo, só aparece com aquele nome específico). Ao mesmo tempo, as tags de escopo daquele cliente aparecem à DIREITA, na mesma linha/altura do nome hovered (não é uma coluna fixa com "as certas acendendo" — as tags simplesmente não existem visíveis até o hover, e aparecem já na posição certa quando ele acontece). Isso corrige a spec antiga da seção 4, que descrevia errado como coluna paralela com tags "acendendo" — na real é mais simples: tags só existem/aparecem no hover, não existem apagadas o tempo todo.
- Aplicar essa mecânica exata no PixelForge, substituindo o texto antigo da seção 4 (Referência Valkiria).

### 11.5 Grid de projetos — hover ok, mas precisa refinar

O conceito de hover (thumb clicável, preview ao passar o mouse) está no caminho certo, mas:
- A thumb estática (frame parado) precisa de um frame melhor, OU voltar a ter uma animação automática em loop tocando por padrão (como era antes), em vez de imagem 100% parada.
- O fade escuro que aparece por cima no hover está forte demais — apaga a visibilidade de quem está tentando ver a prévia em vídeo. Reduzir bastante a opacidade desse overlay.

### 11.6 Seção "Serviços" — formato FECHADO 31/07/2026

**Errado na V1:** entrou como seção de banner na Home, com cards e imagens de exemplo — nada disso é o formato certo. As thumbnails dos 6 serviços também estavam erradas — Ericson ainda não escolheu imagens finais, qualquer imagem que a V1 colocou era placeholder incorreto.

**Correto (substitui a decisão em aberto anterior — Ericson decidiu, não é mais cards):**
- **Não usar formato de card com imagem.** Na Home, a seção Serviços é só uma lista curta com os 6 nomes (Launch Film, 3D Film, Packshot, FOOH, CGI + AI, Pós-produção) — sem imagem, sem resumo, sem explicação nenhuma ali.
- Cada nome, ao clicar, direciona pra a página dedicada daquele serviço (`servicos/[nome].html`, já prevista na seção 5.6/1) — é lá que entra a explicação completa e os exemplos práticos, não na Home.
- **Estilo visual sugerido pelo Ericson:** em vez de lista estática, pensar em algo como uma aba flutuante ou painel com efeito de vidro (glassmorphism) pra dar mais dinâmica — não precisa ser texto plano numa lista comum.
- **Efeito de destaque sugerido:** o efeito de distorção de texto do Lusion (visto no hero da Home deles, seção 9.1.1 — texto que distorce/reage) ainda não foi aplicado em lugar nenhum do site. Um bom lugar pra estrear esse efeito seria no próprio título "Serviços" da seção, ou no hover de cada nome da lista — reforça o "dinamismo" que está faltando (ver 11.11).

### 11.7 "A Forja" — pior correção da rodada, prioridade máxima

Veredito do Ericson: *"essa foi a pior alteração até aqui, completamente distante do que eu quero."*

**Errado na V1:**
- Banner de entrada pequeno, com fade forte demais por cima que praticamente apaga a imagem.
- Foto do Ericson grande demais, ocupando espaço desproporcional.
- Texto da bio pouco legível.
- Efeito de "galeria pinada" saiu completamente errado: preenche só uma parte minúscula da tela, e o resto da seção (bio, foto) some enquanto isso acontece.
- Imagens da galeria aparecem cortadas de forma arbitrária e soltas na composição — "solta na tela assim tá muito feio, mega amadorismo."

**Correto (reforçando a spec original da seção 5.4, que não foi seguida):**
- Banner: aumentar o tamanho, reduzir a intensidade do fade.
- Foto do Ericson: MUITO menor do que está agora.
- Texto da bio: mais legível (contraste, tamanho, espaçamento).
- Efeito de pin: a seção "A Forja" inteira (banner + bio + foto) fica FIXA na tela enquanto, num canto — lado esquerdo, se sobrepondo levemente por cima da foto do Ericson — as imagens da galeria vão trocando uma a uma conforme o usuário rola. A seção continua fixa até todas as imagens passarem; só então libera o scroll e aparece a opção/botão "ver galeria completa". É exatamente como funcionava numa versão anterior já aprovada pelo Ericson — a V1 não seguiu esse comportamento.
- Nenhuma imagem deve aparecer cortada de forma feia ou solta sem enquadramento — todo elemento de imagem precisa de um container/frame definido.

### 11.8 Seção "IA + CGI" — reduzir peso/tamanho

Seção grande/pesada demais. Formato correto: layout split — imagens ocupando metade da tela, texto na outra metade ao lado. Tudo bem menor do que está hoje, mesmo com poucos exemplos de imagem (no futuro entram exemplos em vídeo com IA também, o layout precisa comportar isso sem crescer). Nota geral: essa seção é um exemplo específico de um problema no site inteiro — tudo está pesado/grande demais, precisa de mais leveza e compactação em várias seções, não só aqui.

### 11.9 Rodapé (footer) — vários erros

- Ícones sociais: manter só Instagram, LinkedIn e Behance (remover qualquer outro ícone incorreto que esteja aparecendo).
- Lista de links do rodapé replica os mesmos nomes do nav principal — reduzir, não precisa repetir tudo.
- Em vez de listar todas as seções de novo, colocar um botão "voltar ao topo" que, ao clicar, dispara uma animação de transição (ex: efeito de "desintegrar" a tela) e volta pro início sem obrigar o usuário a rolar manualmente até lá.
- O logo do PixelForge no rodapé precisa SEMPRE ser o logo de verdade (asset gráfico/SVG — `assets/Logo_PixelForge_White.svg` já existe no repo), nunca texto digitado tentando imitar o logo.

### 11.10 Navegação (nav) — consolidar seções da Home

Pra não poluir o nav com um item pra cada seção da Home (Serviços, Projetos, FOOH, IA+CGI, A Forja), consolidar: um único item no nav (ex: "Home") que, ao clicar/passar o mouse, abre um dropdown com as opções de seção pra pular direto (âncora), em vez de cada seção ter seu próprio item de primeiro nível.

### 11.11 Dinamismo geral — falta de animação em todo o site

O site ficou linear/travado, sem o dinamismo das referências (Lusion, seção 9.1.1). Não precisa ser 3D em tudo, mas a experiência de rolar a página precisa parecer convidativa a continuar descendo, não datada/estática. **Exemplo concreto dado pelo Ericson (31/07/2026):** a seção FOOH (seção 5.2) — trocar o carrossel atual (depende de clicar pra avançar) por um carrossel de scroll horizontal (rola direto, sem clique). Ele deixou claro que é só um exemplo entre vários possíveis, e está aberto a mais sugestões — grid de projetos e galeria da A Forja seguem como outros candidatos já registrados. **"Dinamismo" é a palavra-chave de toda essa rodada de revisão** — deve guiar qualquer decisão de animação daqui pra frente.

### 11.12 Página individual de projeto — base boa, transição de entrada fraca

A base da página de projeto (seção 1, template Tendril) já está num caminho legal — reconhecida pelo Ericson como "um começo bem interessante". Conteúdo projeto a projeto é fase futura, não bloqueia agora. Porém, a TRANSIÇÃO de entrada (ao clicar num card do grid pra abrir a página do projeto) está amadora. Ideia sugerida: a própria thumbnail clicada expande e preenche a tela inteira, dando a ilusão de que a mesma imagem está "crescendo" pra virar a página seguinte (mesmo sendo, por baixo, uma troca de página normal) — mesma referência já documentada da transição blur+zoom do Lusion (seção 9.1.1), adaptada pra esse efeito de expansão.

### 11.13 Scroll pra cima não reverte as animações

Problema transversal: ao rolar de volta pra cima, as animações de reveal não voltam ao estado anterior — a página "pula" o efeito, desconfortável quando o usuário quer rever algo que já passou. Correção técnica: qualquer animação de scroll-reveal do site deve usar GSAP ScrollTrigger com `scrub: true` (ou lógica de enter/leave simétrica), não triggers de "tocar uma vez ao entrar em viewport". Vale globalmente — revisar todas as animações do site com esse critério, não só uma seção.

---

## 12. Revisão de implementação V2 — segunda rodada, gravação narrada de ~18min (31/07/2026)

Ericson gravou a tela navegando o site inteiro com narração em áudio, logo após a primeira leva de correções da seção 11. Veredito dele: ainda "muito linear", "seco", falta dinamismo geral — mesmo problema-chave da seção 11.11, ainda não resolvido de forma consistente pelo site inteiro. Vários itens da seção 11 (11.6 distorção de texto, 11.7 A Forja, 11.9 animação do voltar-ao-topo, 11.13 scroll reversível) **ainda NÃO foram aplicados** — não são pedidos novos, são os mesmos de antes confirmados como pendentes. Itens abaixo, na ordem em que ele navegou.

### 12.0 BUG CRÍTICO — reload da página abre no meio do scroll

Confirmado por frame do vídeo (t=0s): ao dar F5/reload, a página carrega já mostrando o meio do grid de projetos (um card do Everlast), não o topo/Hero. Prioridade alta de correção — indício de scroll restoration do navegador não sendo resetado, ou de um hash/anchor na URL, ou de cálculo incorreto de posição inicial do ScrollTrigger. Toda visita/reload precisa abrir no topo (Hero).

### 12.1 Nav — dropdown "Home" não é clicável

O dropdown do nav consolidado (seção 11.10, já implementado visualmente) abre ao passar o mouse, mas ao mover o cursor pra baixo em direção às opções, o menu fecha antes de dar tempo de clicar — provavelmente uma lacuna/gap entre o botão e o dropdown que perde o hover. Corrigir a área de hover (sem gap real entre trigger e menu, ou usar um pequeno delay antes de fechar).

### 12.2 Peça 3D interativa (seção 3.1/11.2) — material ainda não está bom

Ericson reconfirma: o material ainda não ficou legal, mesmo já tendo corrigido a física. Sugestões dele pra explorar (escolher uma, não presumir qual): (a) deixar todas as peças em metal só, sem mistura; (b) alternar as peças entre as cores da marca PixelForge; (c) um material tipo plástico fosco, no estilo do que o Lusion usa. Precisa iterar visualmente com ele antes de fechar.

### 12.3 Marquee "Parcerias Criativas" — pausa estranha, interação desnecessária

Tem uma pausa/momento estranho antes da seção que ele não tem certeza se ficou bom, ligado a uma interação que não deveria existir porque o elemento nem é clicável — remover essa interação/pausa, deixar o movimento contínuo. Tamanho de logo/nome: por ora não mexer mais nisso (não é prioridade nessa rodada).

### 12.4 Seção "Serviços" — falta dinamismo, ajustes de layout

- Segue sem o efeito de distorção de texto (já pedido na seção 11.6) — ainda não implementado.
- Os 6 nomes soltos devem ficar CENTRALIZADOS na seção, dentro de uma caixa/painel mais ao meio da tela (hoje estão distribuídos de forma solta).
- **Tirar a numeração dos setores** (ex: "01", "02" antes do nome de cada serviço) — não fica interessante, e reforça a ideia de ordem/hierarquia que ele não quer (quer algo mais distribuído, sem sensação de lista numerada).
- Efeito vidro/glassmorphism (já pedido na 11.6) segue sem aplicar — visual ainda "bem padrão, bem simples".

### 12.5 Grid de projetos ("Featured Work" / "Projetos que definem padrão")

- Tirar a numeração da seção também (mesmo padrão do item 12.4).
- **Título atual não agrada** ("Trabalho selecionado" ou similar) — trocar por algo "mais elaborado, mais bonito". Não especificou o texto novo, mas deixou claro que o atual não serve.
- A lateral da seção (não especificou qual elemento exatamente, mas mencionou reduzir) pode ficar um pouco menor.

### 12.6 Seção "Clientes/Escopo" — BUG CRÍTICO + vários ajustes

- **BUG CRÍTICO:** durante o scroll, a seção "A Forja" aparece por cima/na frente da seção "Clientes", sobrepondo — torna a seção Clientes inacessível/impossível de usar nesse trecho. Provável conflito de z-index ou de pin entre as duas seções (A Forja provavelmente começando seu próprio pin antes de Clientes liberar o dele). **Prioridade alta.**
- O texto "Clientes" e "Escopo" (cabeçalhos das duas colunas) estão colados demais um no outro — aumentar o espaçamento entre eles.
- **Falta animação de entrada nos nomes dos clientes** — hoje eles simplesmente aparecem "do nada", sem transição. Precisa de uma entrada suave (ele mencionou ter visto uma tentativa de "baixo pra cima" mas achou "muito fraca").
- **A interação de hover não está funcionando de verdade** — os nomes aparecem na posição certa (mecânica da seção 11.4/valkiria), mas passar o mouse não causa nenhuma animação perceptível no próprio nome. Ele quer: ao pairar o mouse sobre um nome, o nome cresce/anima levemente (não só o logo/escopo aparecendo do lado) — reforça a sensação de "roleta" interativa.
- Logo que aparece no hover (à esquerda): está muito pequeno/tímido — aumentar.
- Tags de escopo (à direita, no hover): também muito tímidas — aumentar o tamanho.

### 12.7 Scroll reversível — reconfirmado, ainda não corrigido

Ericson reconfirma o problema já registrado na seção 11.13: ao rolar pra cima, os elementos que já apareceram ficam "pré-carregados" (não voltam ao estado anterior). Ele notou que "uma coisa ou outra" já reverte, mas o padrão geral ainda é só animar na descida. Reforçar a correção da 11.13 — ainda pendente.

### 12.8 "A Forja" — layout ainda errado, spec detalhada de novo

Reconfirmado como a seção mais problemática (crítica já feita na 11.7, correção aplicada não bateu com o esperado):
- Botão "Ver galeria completa": reposicionar pra mais perto de onde as imagens aparecem (hoje está longe/solto). Trocar o texto por algo mais curto, tipo "Ver mais".
- Layout: 50/50 entre texto e imagem — texto mais compacto e alinhado à direita; do lado esquerdo, a foto do Ericson perto do nome dele, e um quadro MAIOR com as imagens de demonstração (galeria), bem mais visível do que está hoje.
- **Nenhum elemento pode ficar colado na borda da tela** — nem a foto dele, nem o quadro da galeria. Dar respiro/margem em volta de tudo.
- A foto dele não pode ficar coberta pela galeria — reposicionar: a foto dele um pouco mais pra cima, o quadro da galeria um pouco mais pra baixo, mesmo tamanho de hoje está ok.
- **Animação de troca de imagem da galeria:** hoje é só uma imagem cobrindo a outra sem transição. Ele quer um efeito tipo "cartas sendo jogadas uma por cima da outra" (ou folhas empilhando) — cada imagem nova entra com uma animação visível por cima da anterior conforme o usuário rola, não um corte seco.

### 12.9 Seções em geral — remover numeração e títulos genéricos

Padrão que se repete em várias seções (Serviços, Grid de projetos, e possivelmente outras): tirar qualquer numeração de setor ("01 —", "03 —" etc.) — não combina com a ideia de site dinâmico/não-linear que ele quer. Títulos de seção genéricos como "Trabalho selecionado" precisam ser reescritos pra algo mais elaborado — revisar título por título depois que o layout estiver mais avançado.

### 12.10 FOOH — scroll horizontal atual não ficou bom, spec de coverflow

O carrossel horizontal implementado (resposta à sugestão da seção 11.11) ficou "seco", "muito simples" — "trava em cima e rola pro lado, não tá legal". **Nova spec, mais detalhada:**
- Manter texto à esquerda, vídeos à direita (como já era).
- Mostrar **3 vídeos por vez, estilo coverflow**: o do meio em destaque (tamanho normal, brilho/opacidade total), os das duas pontas menores, um pouco atrás (profundidade) e mais apagados/opacos.
- Ao rolar, avança um vídeo por vez — como se a pessoa "parasse pra assistir cada um" antes de ir pro próximo.
- A seção fica PINADA (fixa) durante esse trecho de rolagem horizontal, e só libera o scroll vertical normal depois que os vídeos terminam de passar.

### 12.11 Seção "IA + CGI" — formato aprovado, falta animação + variar imagens

Ericson gostou do formato atual (compacto, "tímido" no bom sentido) — só falta animação de entrada nele. Ideia nova: em vez de um quadro fixo com 4 imagens estáticas, ter um banco maior (~20 imagens de trabalhos reais de CGI+IA) alternando dentro das mesmas 4 posições do quadro, trocando periodicamente.

### 12.12 CTA final — aprovado, sem mudanças

Funcionando bem, sem crítica.

### 12.13 Botão "Voltar ao topo" — sem efeito, reforça pedido da 11.9

Clicou e não tem nenhum efeito de transição — só pula direto pro topo. Reforça o pedido já registrado na seção 11.9: quer um efeito de "desfazer/desintegrar em pixels" na tela durante essa transição, não um pulo seco.

### 12.14 Logo no rodapé — trocar pela versão com a tarja colorida

O logo atual no rodapé está ok, mas ele quer especificamente a versão do logo **com a tira/tarja colorida** (ele vai localizar o arquivo certo na pasta dele e enviar pra substituição — não presumir qual arquivo é, aguardar ele confirmar).

### 12.15 Links sociais do rodapé/nav — destinos corrigidos

- **Instagram:** trocar de `@pixelforgestudio` (perfil da marca, inativo no momento) para o Instagram PESSOAL dele, `@borbasmith`. Isso é temporário — quando ele reativar o perfil da marca no futuro, pode reverter.
- **LinkedIn:** manter como está, direcionando pra página da PixelForge — sem mudança.
- **Behance:** trocar de página da marca PixelForge para a página PESSOAL dele no Behance (ele confirma que já tem o link em contexto de conversas anteriores; se não tiver, pedir a ele reenviar). É a mesma página pra onde os cliques dos projetos do grid já apontavam no site antigo.

### 12.16 CTA duplo — botão de baixo não funciona

Existem dois pontos de CTA pra contato: o botão "Contato" no nav (topo) e um botão equivalente mais abaixo na página (provavelmente o CTA final da seção 5.5 ou o "Iniciar projeto"). Só o de cima está funcionando — o de baixo não responde ao clique. Os dois precisam ter exatamente o mesmo destino/funcionalidade.

### 12.17 Formulário de contato (Formspree) — pendência, não mexer agora

Configuração de pra qual e-mail o formulário envia ainda não está confirmada/testada. Ericson sinalizou que isso fica pra depois, não é prioridade dessa rodada — só registrar como pendência aberta, não implementar mudança agora.

### 12.18 Páginas de Serviços (hub + individuais) — estrutura aprovada, conteúdo com erros pontuais

**A proposta de página isolada por serviço está exatamente como ele queria** — elogio direto, manter a estrutura. Problemas específicos de conteúdo, não de estrutura:
- **"3D Film":** o vídeo de exemplo usado está completamente errado (não representa 3D Film de verdade) — trocar por exemplo correto.
- O card/preview de cada serviço (provavelmente no cross-link do rodapé de cada página de serviço, seção 5.6) não está visualmente legal — melhorar.
- **FOOH:** normalmente é veiculado em formato vertical (retrato), mas a página está tratando/exibindo em formato horizontal — ajustar orientação da mídia pra bater com o formato real de uso.

### 12.19 Navegação "voltar pra Home" recarrega tudo do zero

Ao voltar da página de um serviço (ou de projeto) pra Home, a página inteira recarrega do zero (perde tempo de load) — incomoda. Considerar navegação sem reload completo (cache, ou transição que evite recarregar assets pesados de novo) — sinalizado como incômodo, não necessariamente bloqueador.

### 12.20 Transição entre páginas de projeto — fluida mas genérica

A transição ao navegar entre projetos individuais é fluida (sem travar), mas "não tem nada de original, é bem simples" — mesma crítica de falta de dinamismo das outras seções, só que aqui é menor prioridade porque pelo menos funciona bem. Melhorar quando der, não é bloqueador.

### 12.21 Página de projeto individual — estrutura APROVADA

Ericson confirmou que gostou do formato base da página de projeto — "bem simples, mas é isso mesmo que eu queria". Ações concretas:
- **Manter o botão que já existe na página** (o de ação/link principal do projeto) — ele quer esse mesmo botão em todos os projetos futuros, tanto na Home quanto nas páginas internas.
- Para o texto de cada projeto: reaproveitar o conteúdo que já existe no CV dele (`cv-ericson-borba.html`, já presente no repo) como base de texto pronta — copiar/adaptar de lá pra cá em vez de escrever do zero, "porque funciona perfeitamente". Pode precisar de um texto extra aqui e ali, mas a base já está pronta e aprovada.
- Vai ter mais imagens e mais texto por projeto no futuro — isso é esperado, não é problema da estrutura atual.

### 12.22 Contexto de prazo (31/07/2026)

Ericson entra essa semana com força em duas frentes: prospecção de clientes novos, e busca de parceiros/estúdios — incluindo possivelmente estúdios de Portugal, destino pra onde ele planeja se mudar no próximo ano. Motivo pelo qual quer o site bem polido o quanto antes — não é só preferência estética, é ferramenta ativa de prospecção a partir de agora.
