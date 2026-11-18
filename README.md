# InovaCity

**Conectando pessoas. Transformando cidades.**

InovaCity é uma plataforma de participação cidadã para a infraestrutura urbana. A pessoa registra um problema do bairro, como buraco, poste apagado, lixo acumulado, alagamento ou calçada sem acessibilidade. A plataforma organiza e prioriza o relato com apoio de inteligência artificial e mostra o andamento a quem relatou. Projeto da FIAP, Global Solution 2026.2 – CitizenTech.

Autores: Rodrigo Wolkoff Giorgi (RM 556980) e Carlos Eduardo Mamede (RM 568269).

## O problema

Problemas pequenos de infraestrutura costumam ser relatados de forma dispersa: ligação, rede social, grupo de moradores. Não há protocolo, prioridade nem retorno. Quem mais sente são pessoas com mobilidade reduzida, idosos e quem circula à noite. As equipes de manutenção recebem informação repetida e sem critério de urgência.

## O que a plataforma faz

| Parte | O que faz | Página |
|---|---|---|
| Portal do cidadão | Cadastro de ocorrência, consulta do andamento e painel do bairro. Instalável como aplicativo (PWA). | Início, Nova ocorrência, Consultar, Painel |
| Robô de triagem (RPA) | Lê um CSV de ocorrências, valida, classifica, agrupa duplicatas, define prioridade e notifica. O que o robô não resolve vai para uma pessoa. | Robô |
| InovaBot | Responde dúvidas com base em documentos oficiais e mostra a fonte de cada resposta. | InovaBot |
| Placa de sensores (IoT) | ESP32 com sensor de temperatura e umidade (DHT22) e de distância (HC-SR04) publica leituras por MQTT. O alerta exige três leituras seguidas e validação humana. | Placa |
| Imagens e vídeos (Visão) | Recebe uma foto ou vídeo e, quando há modelo treinado, sugere a categoria do dano com caixas e confiança. | Imagens |
| Relatos e Fábrica de Corpus (PLN) | Analisa relatos e gera conjuntos de dados em JSONL a partir de documentos públicos, com anonimização. | Relatos, Corpus |
| Estudos | Cluster e computação neuromórfica (simulação) e computação quântica (proposta de roadmap). | Relatórios das disciplinas |

Nada disso substitui a vistoria técnica nem a decisão do poder público. A plataforma organiza e prioriza, e uma pessoa decide quando há dúvida.

## Controles de governança

- Revisão humana dos casos de baixa confiança e dos alertas de sensor.
- Quarentena de linhas inválidas, com o motivo registrado.
- Anonimização de CPF, CNPJ, e-mail, telefone e nomes antes de gerar arquivos.
- Fontes visíveis nas respostas do InovaBot.
- Dados simulados identificados como simulados no próprio site.

## Estado atual

Os dados de teste são sintéticos ou simulados. Os resultados mostram que os fluxos funcionam, não a qualidade com dados reais.

- Robô: 51 linhas lidas, 32 processadas, 12 em revisão humana, 4 em quarentena, 3 duplicatas.
- InovaBot: fonte correta entre os 3 primeiros em 91% de 75 perguntas dentro do escopo.
- Visão: YOLOv8n com mAP50 de 0,333 no teste.
- Computação quântica: proposta, sem implementação.

## Marca

| Elemento | Detalhe |
|---|---|
| Símbolo | Duas figuras (azul e laranja) abraçando a cidade, prédios, linhas de circuito e arco de sinal sem fio. Um arco verde-azulado envolve a cena. |
| Nome | "Inova" em azul-marinho e "City" em verde-azulado |
| Mascote | InovaBot, o assistente do site |
| Azul-marinho | `#012B58`, cor institucional |
| Verde-azulado | `#039882`, cor de apoio |
| Laranja | `#FB6702`, cor de ação |
| Fundo do site | `#F7F4EC` (papel) e `#FFFDF6` (cartão) |
| Fontes do site | Fredoka (títulos) e Nunito (texto), da Google Fonts, licença SIL OFL 1.1 |

O site tem modo de alto contraste e três tamanhos de texto.

## Como rodar

```
pip install -r requirements.txt
python servidor.py
```

Abra o endereço que o servidor mostrar no terminal. O InovaBot funciona em modo extrativo sem modelo de linguagem. O modo generativo usa o Qwen 2.5 7B pelo Ollama, se estiver instalado.

## Repositórios

- Front End (plataforma): https://github.com/fiap-projectxs/InovaCity-GS-FrontEnd
- RPA: https://github.com/fiap-projectxs/InovaCity-GS-RPA
