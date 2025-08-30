## Visão Geral do Projeto "Sem Rumo"

Este documento fornece uma visão geral e o contexto fundamental do projeto "Sem Rumo", servindo como referência para todas as interações e desenvolvimentos.

**1. Motivações e Objetivos:**

*   **Aprendizado e Desenvolvimento:** Treinar habilidades de desenvolvimento Web, com foco na interação e aproveitamento de modelos de linguagem (LLMs) como o Manus.
*   **Diversão e Interação Social:** Criar uma plataforma para entretenimento e interação com amigos, centrada no grupo de samba amador "Sem Rumo".

**2. Conceito Principal: "Web Rádio" de Samba ao Vivo:**

O projeto visa criar um site simples para transmitir performances do grupo "Sem Rumo" ao vivo, permitindo que amigos (mesmo à distância) assistam/ouçam e interajam.

**3. Abordagens de Transmissão (Atuais e Futuras):**

*   **Live com Câmera do Celular (YouTube/Twitch):**
    *   **Descrição:** Transmissão de vídeo e áudio via câmera de celular para plataformas como YouTube ou Twitch.
    *   **Integração:** O site exibe o player da live (via parâmetros `?yt=` ou `?twitch=`).
    *   **Status:** Parcialmente implementada e funcional.

*   **Live como "Web Rádio" (Microfone do Notebook e Tela):**
    *   **Descrição:** Transmissão focada em áudio (microfone do notebook) com a tela do computador como visual de fundo.
    *   **Ferramentas Necessárias:** Software de transmissão (ex: OBS Studio) para capturar áudio e tela, enviando para YouTube/Twitch.
    *   **Status:** Ideia em desenvolvimento, com foco em superar desafios como ruído ambiente.

**4. Solução para Ruído Ambiente: Voz Sintetizada (Text-to-Speech - TTS):**

*   **Desafio:** Vizinhança sensível impede o uso constante de microfone em certos horários.
*   **Solução:** Utilizar TTS para a "locução" da rádio, transformando uma limitação em uma característica.
*   **Vantagens:** Contorno do ruído, fluidez, consistência, possibilidade de conteúdo pré-programado (vinhetas, anúncios), acessibilidade.

**5. Ideias Inovadoras para a "Web Rádio":**

*   **Interface de Controle para TTS:**
    *   **Conceito:** Aplicação web para gerenciar a "locução", com botões para textos pré-definidos e campo para digitação ao vivo.
    *   **Benefícios:** Agilidade, consistência, foco na interação.

*   **Avatar "Max Headroom" (VJ Virtual):**
    *   **Conceito:** Criação de um avatar vintage para ser o "rosto" da rádio, justificando a voz sintetizada.
    *   **Animações:** Animações básicas (sincronia com áudio) e contextuais (dança, surpresa) para engajamento visual e identidade única.

**6. Estrutura do Repositório e Persistência de Contexto:**

*   **Localização:** Repositório GitHub `robertocunha/sem-rumo`.
*   **Arquivos de Contexto:**
    *   `project_overview.md` (este arquivo): Informações gerais e estáticas do projeto.
    *   `latest_session_notes.md` (anteriormente `context_summary.md`): Resumo das últimas discussões, novas ideias, decisões e próximos passos de cada sessão de chat.
*   **Mecanismo de Persistência:** O contexto é mantido no repositório remoto, permitindo que o Manus (ou qualquer colaborador) clone o repositório e acesse as informações em qualquer nova sessão de trabalho.

---

