# FIAP - Faculdade de Informática e Administração Paulista
   
<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# 🧠 FarmTech Solutions: O despertar da Rede Neural

## Turma: FIAP-1TIAOB

## 👨‍🎓 Integrantes: 
- Samyr de Souza Pereira
- Antonio Filipe de Souza Branco
- Albert Oliveira Ribeiro
- Vinicius Seiti Adati

## 👩‍🏫 Professores:
### Tutor(a) 
- <a href="https://www.linkedin.com/company/inova-fusca">Sabrina Otoni</a>
### Coordenador(a)
- <a href="https://www.linkedin.com/company/inova-fusca">André Godoi Chiovato</a>


## 📜 Visão Geral

Projeto da **Fase 6 (O começo da rede neural)**. A FarmTech Solutions está expandindo seus serviços de IA para além do agronegócio e quer mostrar a um cliente como funciona, na prática, um sistema de visão computacional. Para isso, treinamos o **YOLOv5** para detectar dois objetos bem diferentes, **vaca** e **bicicleta**, e comparamos duas simulações de treino.

- 👉 **Notebook completo (Google Colab):** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/brancofelipe641-jpg/FarmTech-Fase6-Cap-1---O-despertar-da-Rede-Neural/blob/main/src/AntonioFilipeDeSouzaBranco_rm573837_pbl_fase6.ipynb)
- 🗂️ **Dataset e resultados no Drive:** https://drive.google.com/drive/folders/1gz_ejuuDiEIgJNe1DnIa7cBvoya6AeVr?usp=drive_link
  
O passo a passo, o código comentado, os resultados e as conclusões completas estão no notebook.

### 🖼️ Dataset

- 80 imagens (40 de vacas e 40 de bicicletas), usadas exclusivamente para fins acadêmicos (fontes: magnific.com e pinterest.com).
- Divisão por classe: 32 imagens para treino, 4 para validação e 4 para teste (64, 8 e 8 no total).
- Rotulação feita no site Make Sense, com caixas em cada objeto e exportação no formato YOLO (classe 0 = vaca, classe 1 = bicicleta).

### 🧠 Metodologia

Partimos do modelo pré-treinado `yolov5s` (transfer learning) e o treinamos com as nossas imagens no Google Colab, com GPU Tesla T4. Foram feitas duas simulações, com **30** e **60 épocas**, e cada uma foi avaliada na validação e em imagens de teste nunca vistas pelo modelo.

### 📈 Curvas de treino

Perdas (box, obj e cls) e métricas (precisão, recall e mAP) ao longo das épocas, medidas na validação.

**30 épocas**

<img src="assets/results_30ep.png" width="80%">

**60 épocas**

<img src="assets/results_60ep.png" width="80%">

### 📊 Resultados no conjunto de teste

| | 30 épocas | 60 épocas |
|---|---|---|
| Precisão | 0,842 | 0,899 |
| Recall | 0,964 | 0,713 |
| mAP50 | 0,995 | 0,912 |
| mAP50-95 | 0,649 | 0,736 |
| Tempo de treino | 0,177 h | 0,348 h |
| Detecções nas 8 imagens (confiança mínima 0,25) | 7 de 8 | 8 de 8, com 1 caixa duplicada |

### 🔎 Principais achados

- Os dois modelos aprenderam a distinguir vaca de bicicleta com apenas 64 imagens de treino.
- **Não houve um vencedor claro:** o modelo de 60 épocas desenhou caixas mais justas nas vacas, mas custou o dobro do tempo de treino e gerou uma caixa duplicada. O de 30 épocas perdeu uma bicicleta com o limiar de 0,25.
- A bicicleta foi mais difícil de detectar que a vaca (confiança mais baixa nos dois modelos).
- A validação foi otimista, porque o melhor modelo foi escolhido com base nela. O teste é a medida mais confiável.

## 📁 Estrutura de pastas

Dentre os arquivos e pastas presentes na raiz do projeto, definem-se:

- <b>.github</b>: Nesta pasta ficarão os arquivos de configuração específicos do GitHub que ajudam a gerenciar e automatizar processos no repositório.

- <b>assets</b>: aqui estão os arquivos relacionados a elementos não-estruturados deste repositório, como imagens.

- <b>config</b>: Posicione aqui arquivos de configuração que são usados para definir parâmetros e ajustes do projeto.

- <b>document</b>: aqui estão todos os documentos do projeto que as atividades poderão pedir. Na subpasta "other", adicione documentos complementares e menos importantes.

- <b>scripts</b>: Posicione aqui scripts auxiliares para tarefas específicas do seu projeto. Exemplo: deploy, migrações de banco de dados, backups.

- <b>src</b>: notebook com a solução da Fase 6.

- <b>README.md</b>: arquivo que serve como guia e explicação geral sobre o projeto (o mesmo que você está lendo agora).

## 🔧 Como executar o código

**Pré-requisitos:** conta Google (Colab e Drive). Versões usadas: Python 3.13, PyTorch 2.11 e YOLOv5 v7.0.

1. Abra o notebook no Colab pelo botão da seção Descrição.
2. Abra a pasta do Drive, clique com o botão direito em `FarmTech_Fase6`, escolha **Organizar > Adicionar atalho ao Drive** e selecione "Meu Drive".
3. No Colab, ative a GPU em *Ambiente de execução > Alterar tipo de ambiente de execução > T4*.
4. Execute as células em ordem. As saídas dos treinos já estão salvas no notebook (cerca de 11 e 21 minutos de treino).

## 🎥 Vídeo de demonstração

O vídeo tem até **5 minutos** e demonstra o funcionamento do notebook, do dataset até as conclusões.

**YouTube (não listado):** COLE_AQUI_O_LINK_DO_VIDEO

## 🧪 Limitações atuais

- Dataset pequeno, conforme proposto no enunciado (40 imagens por classe). Com validação e teste de apenas 8 imagens, cada erro pesa muito nas métricas.
- As fotos de teste são quase todas close-ups ou imagens de produto, sem vacas ao longe, rebanhos ou bicicletas parcialmente visíveis.
- A confiança das detecções é baixa (entre 0,29 e 0,73), e o resultado depende do limiar de confiança escolhido.
- A espessura das linhas e o tamanho do texto nas imagens de detecção dependem da resolução original de cada foto, então em algumas bicicletas o rótulo aparece cortado. As caixas e as confianças não são afetadas.
- Esta entrega cobre o YOLOv5 customizado (Entrega 1). A comparação com o YOLO padrão e com uma CNN treinada do zero (Entrega 2, "Ir Além") fica como trabalho futuro.

## 🗃 Histórico de lançamentos

* 1.0.0 - XX/10/2026
    * Entrega 1: YOLOv5 customizado, com simulações de 30 e 60 épocas
      
## 📋 Licença

<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/agodoi/template">MODELO GIT FIAP</a> por <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://fiap.com.br">Fiap</a> está licenciado sobre <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International</a>.</p>


