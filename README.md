# 🏛️ Museu VR — Segurança Digital

> **Projeto Final: Meu Primeiro Ambiente VR Interativo**  
> Web 3.0 | Residência em TIC 29 — Unidade 1, Capítulo 3  
> Disciplina: Fundamentos do Metaverso

---

## 👤 Autor

**Nome:** Francisco Janiel Gomes Rodrigues
**Turma:** Web 3.0 — Residência em TIC 29  
**Professora:** Ana Beatriz

---

## 🎯 Apresentando o Seu Projeto

O **Museu VR de Segurança Digital** é um ambiente virtual imersivo desenvolvido em Unity 6 LTS, voltado para a **educação em cibersegurança através do metaverso**. O visitante navega livremente por uma galeria temática que contém **5 estações educativas**, cada uma representada por um **avatar humanoide (guia virtual)** que apresenta informações sobre um tema crítico de segurança digital quando interagido.

### Estações implementadas

| Estação | Tema | Cor de Identificação |
|---|---|---|
| 🔵 **Senhas** | Boas práticas de senhas seguras | Azul |
| 🔴 **Phishing** | Identificação de e-mails maliciosos | Vermelho |
| 🟢 **2FA** | Autenticação em Dois Fatores | Verde |
| 🟡 **LGPD** | Lei Geral de Proteção de Dados | Amarelo |
| 🟣 **Engenharia Social** | Manipulação psicológica em ataques | Roxo |

### Funcionalidades principais

- ✅ **Navegação livre 360°** pelo museu com WASD + mouse (sem necessidade de óculos VR)
- ✅ **5 avatares humanoides** posicionados nas estações temáticas
- ✅ **Interação por clique** — ao clicar em um avatar, aparece um **balão de fala 3D flutuante** acima da cabeça dele
- ✅ **Sistema de tracking** que registra quantas estações o visitante já explorou (1/5, 2/5... 5/5)
- ✅ **Feedback sonoro** em todas as interações (beep procedural gerado em tempo real)
- ✅ **Skybox dourado de Golden Hour** para criar atmosfera acolhedora
- ✅ **Iluminação direcional quente** simulando luz natural de fim de tarde

---

## 🌐 Contexto e Objetivos no Metaverso

### Que problema o projeto resolve?

A **educação em cibersegurança** enfrenta um desafio recorrente: o tema é técnico e abstrato, o que dificulta o engajamento de estudantes e do público em geral em palestras puramente expositivas. Conceitos como phishing, autenticação em dois fatores e engenharia social parecem distantes do dia a dia até que algo dê errado.

Este projeto propõe uma alternativa imersiva: transformar conceitos abstratos em uma **experiência espacial navegável**, onde o visitante explora os temas no próprio ritmo, "conversa" com guias virtuais e visualiza cada tópico como uma estação física. A abordagem se alinha perfeitamente ao tema central da Residência em TIC 29 (**Web 3.0**), reforçando a importância da consciência digital em uma era de identidades descentralizadas, dados pessoais como ativos e novos vetores de ataque.

### Categoria no Metaverso

O projeto se enquadra na categoria **educação imersiva** dentro do conceito amplo de metaverso. Pode ser utilizado por:

- 🏫 **Escolas e universidades** — em aulas remotas ou presenciais de TI/segurança
- 🏢 **Empresas** — para treinamentos corporativos de conscientização em segurança
- 👨‍👩‍👧 **Famílias** — para introduzir crianças e adolescentes aos riscos digitais
- 🌍 **Comunidades remotas** — onde acesso a educação especializada é limitado

### Objetivo educacional

Demonstrar que ambientes 3D interativos podem **complementar (não substituir)** o aprendizado tradicional, oferecendo um espaço onde o visitante:

1. Move-se livremente, criando memória espacial associada ao conteúdo
2. Escolhe a ordem das estações, respeitando seu próprio ritmo
3. Recebe feedback imediato (visual + sonoro) a cada interação
4. Vê o progresso de forma clara (contador 5/5)

---

## 🛠️ Processo de Criação e Dificuldades

### Stack técnico

- **Motor:** Unity 6 LTS (versão 6000.4.3f1)
- **Render Pipeline:** Universal Render Pipeline (URP)
- **SDK XR:** XR Interaction Toolkit 3.4.1 (Unity oficial)
- **Linguagem:** C# (5 scripts customizados)
- **Asset externo:** Low Poly People por David Jalbert (Asset Store, gratuito)
- **Sistema de input:** Both (Input Manager Legacy + Input System novo)

### Scripts implementados

| Script | Função |
|---|---|
| `GameManager.cs` | Singleton de gerenciamento global, conta estações visitadas |
| `BalaoDeFala.cs` | Detecta clique em avatares e exibe balão de fala 3D |
| `InteracaoSimples.cs` | Sistema alternativo de interação por Raycast |
| `CameraPCMovimento.cs` | Movimentação FPS com rotação 360° livre |
| `RotacaoSuave.cs` | Animação procedural de flutuação/rotação |
| `EstacaoInterativa.cs` | Versão XR Toolkit das estações (reserva para futuro Quest) |

### Etapas do desenvolvimento

1. **Setup inicial** — Instalação do Unity 6 LTS com módulos Android, criação do projeto Universal 3D
2. **Configuração XR** — Instalação do XR Interaction Toolkit, migração para o novo Input System
3. **Modelagem do espaço** — Construção do museu com primitivos (1 piso + 4 paredes)
4. **Estações temáticas iniciais** — 5 cubos coloridos com Box Collider e scripts customizados
5. **Sistema de interação em C#** — Implementação de Raycast do mouse + feedback visual/sonoro
6. **Tracking de progresso** — GameManager singleton com contador de visitas
7. **Skybox dourado** — Criação de material Procedural Skybox customizado para Golden Hour
8. **Importação de avatares** — Asset "Low Poly People" do David Jalbert via Asset Store
9. **Conversão de materiais** — Render Pipeline Converter (Built-in → URP) para 10 materiais
10. **Substituição dos cubos por avatares humanoides** — 5 bonecos posicionados nas estações
11. **Balões de fala 3D** — Sistema de TextMesh flutuante com billboard (sempre olha para a câmera)
12. **Rotação 360° livre** — Refatoração do CameraPCMovimento para FPS sem trava de yaw
13. **Testes finais** — Validação de todas as 5 interações no Editor

### Maiores dificuldades enfrentadas

#### 1. Conflito entre Input System antigo e novo

**Problema:** Ao instalar o XR Interaction Toolkit, o Unity migrou automaticamente o projeto para o novo Input System. Isso quebrou os scripts de movimentação que usavam `Input.GetAxis()` e `Input.GetKey()` do sistema legado, gerando `InvalidOperationException` em tempo de execução.

**Solução:** Em `Edit → Project Settings → Player → Active Input Handling`, alterei o valor para `Both`, permitindo a coexistência dos dois sistemas. Isso preservou os scripts legados sem comprometer a integração com o XR Toolkit.

#### 2. Materiais "rosa choque" do asset baixado

**Problema:** Após importar o pacote "Low Poly People" da Asset Store, todos os bonecos apareciam em rosa magenta — o shader Standard do pacote original não é compatível com URP.

**Solução:** Utilizei o `Window → Rendering → Render Pipeline Converter` com os conversores **Material Reference Converter** e **Material Shader Converter** habilitados. Em uma única operação, 10 materiais foram convertidos de Built-in para URP Lit com sucesso.

#### 3. Rotação travada da câmera (não conseguia olhar para os lados)

**Problema:** O script inicial de movimentação tentava aplicar a rotação horizontal no "pai" do GameObject (`transform.parent.Rotate()`), mas a Main Camera não tinha pai — então a câmera só conseguia inclinar para cima/baixo, sem rotação 360°.

**Solução:** Refatorei o `CameraPCMovimento.cs` para acumular as rotações de yaw e pitch em variáveis internas e aplicá-las diretamente via `Quaternion.Euler()`. O resultado foi uma câmera FPS de rotação 360° livre, com limite vertical de 85° para evitar inversão.

#### 4. Avatares sem animação (T-pose persistente)

**Problema:** Embora o pacote do David Jalbert mencionasse "4 animations included (idle, walk, run, wave)", as animações estavam em arquivos `.anim` separados em `Prefabs/Animations/`, não embutidas nos FBX. Além disso, os modelos vieram com Animation Type "Generic", que limitava a compatibilidade.

**Solução parcial:** Mudei o Animation Type para `Humanoid` na aba Rig do FBX, criei o avatar com `Create From This Model`, e apliquei o Animator Controller `normal` nos bonecos. A complexidade de configuração entre Generic/Humanoid e referências quebradas no Avatar levou à decisão de manter os bonecos em pose estática (T-pose), tratados conceitualmente como **estátuas educativas do museu** — uma escolha narrativa coerente com o tema "museu".

#### 5. Boneco filho de uma estação herdando o script de rotação

**Problema:** Ao arrastar o primeiro boneco para a Hierarchy, soltei dentro de uma estação por engano. O boneco se tornou filho do cubo e começou a "girar suavemente" junto, comportamento herdado do script `RotacaoSuave` aplicado ao cubo pai.

**Solução:** Arrastei o boneco para fora da estação no painel Hierarchy, isolando-o no nível raiz da cena. Aprendizado importante sobre como o sistema de hierarquia do Unity propaga transformações.

### Aprendizados principais

- **Hierarquia importa:** a estrutura de GameObjects pai/filho afeta diretamente transformações, scripts e renderização
- **Pipeline matters:** Built-in, URP e HDRP não são intercambiáveis — assets precisam ser convertidos
- **Padrão Singleton em C#:** o GameManager usa esse padrão para acesso global sem acoplamento
- **Raycast é fundamental em XR:** quase toda interação no XR Interaction Toolkit é baseada em raios da câmera/controle
- **Iteração rápida funciona melhor:** começar com primitivos coloridos e depois substituir por modelos detalhados acelerou muito o desenvolvimento

---

## 🎮 Como executar o projeto

### Pré-requisitos
- Unity 6 LTS (6000.0 ou superior)
- Sistema operacional: Windows / Mac / Linux

### Passos
1. Clone este repositório ou baixe como ZIP
2. Abra o **Unity Hub** → clique em **Open** → selecione a pasta do projeto
3. Aguarde a importação dos pacotes (3-5 minutos na primeira vez)
4. No painel **Project**, abra `Assets/Scenes/SampleScene.unity`
5. Aperte **Play ▶️** no topo do editor

### Controles
| Tecla | Ação |
|---|---|
| `W` `A` `S` `D` | Movimentar-se pelo museu |
| `Mouse` | Olhar ao redor (360° livre) |
| `Espaço` | Subir (voar) |
| `Shift` | Descer |
| `Botão esquerdo do mouse` | Interagir com avatares |
| `ESC` | Liberar/travar o cursor |

### Como interagir
1. Use **WASD** para se aproximar de qualquer avatar
2. Centralize a câmera (mira invisível) no torso do boneco
3. **Clique com o botão esquerdo do mouse**
4. Um balão de fala 3D aparecerá acima do boneco com o conteúdo educativo
5. O balão desaparece automaticamente após 8 segundos
6. Visite todos os 5 avatares para completar o tour (Console mostra "5/5")

---

## 📂 Estrutura de pastas

```
museu-vr-seguranca-digital/
├── Assets/
│   ├── Scripts/                  # Todos os scripts C# do projeto
│   │   ├── GameManager.cs
│   │   ├── BalaoDeFala.cs
│   │   ├── InteracaoSimples.cs
│   │   ├── CameraPCMovimento.cs
│   │   ├── RotacaoSuave.cs
│   │   ├── EstacaoInterativa.cs
│   │   └── Materials/            # Materiais criados (piso, paredes, skybox)
│   ├── Scenes/
│   │   └── SampleScene.unity     # Cena principal do museu
│   ├── DavidJalbert/             # Pacote de bonecos low poly (Asset Store)
│   ├── Settings/                 # Configurações URP
│   └── XRI/                      # Configurações XR Interaction Toolkit
├── ProjectSettings/              # Configurações de Build, Player, XR
├── Packages/                     # manifest.json com dependências
├── .gitignore                    # Ignora /Library, /Temp, /Build, etc.
└── README.md                     # Este arquivo
```

---

## 🔮 Melhorias futuras planejadas

- 🎬 **Animações idle** funcionais nos bonecos (resolver questão Generic/Humanoid)
- 🎨 **Estações temáticas elaboradas** — substituir bonecos isolados por cenários completos (mesa, laptop, livros)
- 💡 **Iluminação cinematográfica** — Point Lights coloridas em cada estação com a cor do tema
- 🎮 **Sistema de quiz interativo** — pergunta de múltipla escolha em cada estação com pontuação
- 🌐 **Build WebGL** — versão acessível diretamente pelo navegador, sem necessidade de instalação
- 🥽 **Suporte completo a Meta Quest** — migração do Mock HMD para hardware VR real via Meta XR SDK
- 🔊 **Narração com áudio** — locução em português para acessibilidade
- 🌍 **Multiplayer** — turmas inteiras visitando simultaneamente via Photon PUN2

---

## 🙏 Créditos

- **Avatares low-poly:** [David Jalbert — Low Poly People](https://assetstore.unity.com/) (Asset Store, gratuito)
- **Motor de jogo:** [Unity Technologies](https://unity.com)
- **XR Interaction Toolkit:** [Unity oficial](https://docs.unity3d.com/Packages/com.unity.xr.interaction.toolkit@3.4/manual/index.html)

---

## 📄 Licença

Projeto acadêmico desenvolvido para a Residência em TIC 29 — Web 3.0.  
Uso livre para fins educacionais e de portfólio.

---

**Desenvolvido com 💙 para a Residência em TIC 29 — Web 3.0**
