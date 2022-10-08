# Music is Data: Uma introdução à recuperação de informações musicais (MIR) - análise e categorização de dados musicais


#### Aluno: [Luis Claudio Santos Arcos](https://github.com/lcarcos) 

#### Orientadora: [Professora Evelyn Batista](https://github.com/evysb)  

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão". 

### Resumo 

A recuperação de informações musicais, ou MIR - Music Information Retrieval, é a ciência de analisar e categorizar dados musicais. MIR é um campo de pesquisa crescente, com muitas aplicações no mundo real. Sistemas de recomendação musical são exemplos de aplicação. A plataforma de streaming de música Spotify aplica técnicas de inteligência artificial para análise de áudio e disponibiliza acesso a esses dados através de sua API da Web. Esse trabalho apresenta o desenvolvimento de uma aplicação de análise e categorização de dados musicais utilizando Python e a API da Web do Spotify.

### Abstract 

Music Information Retrieval, or MIR, is the science of analyzing and categorizing musical data. MIR is a growing field of research with many real-world applications. Music recommendation systems are examples of application. The music streaming platform Spotify applies artificial intelligence techniques to audio analysis and provides access to this data through its web API. This work presents the development of an application for analyzing and categorizing musical data using Python and Spotify web API.

### 1. Introdução 

Provavelmente, você está inscrito em algum tipo de serviço popular de streaming de música. Seja Spotify, Deezer ou Apple Music, você provavelmente já foi exposto a um aplicativo de recuperação de informações musicais. 

A recuperação de informações musicais (music information retrieval) é a ciência de analisar e categorizar dados musicais. Algumas aplicações do MIR estão intimamente relacionadas ao campo da ciência de dados, ao mesmo tempo em que combinam vários campos, como psicoacústica, processamento de sinais, aprendizado de máquina e inteligência computacional. O MIR é um campo de pesquisa crescente, com muitas aplicações no mundo real. Sistemas de recomendação musical são exemplos de aplicação. 

O Spotify é um serviço de música muito popular que aplica técnicas de aprendizagem de máquina para análise de áudio e recuperação de informações musicais.  Felizmente, o Spotify disponibiliza esses dados através de sua API da Web. É possível explorar as características do áudio e analisar detalhadamente as faixas.

Algumas dessas características poderiam explicar o porquê de algumas músicas serem mais ou menos populares. Essa análise é especialmente útil para músicos, gravadoras e distribuidores de música, que podem optar por investir recursos limitados (campanhas publicitárias, equipamento de estúdio, etc.) em faixas que provavelmente se tornarão populares.

O objetivo desse trabalho é a criação de uma aplicação de análise e categorização musical baseado no sistema de recomendação do Spotify. Utilizaremos Python e o API do Spotify em nosso desenvolvimento. 

Nesse trabalho, utilizaremos como exemplo a artista Anitta. Queremos buscar suas músicas mais populares, oferecendo uma análise visual das características do áudio.

<div style="page-break-after: always;"></div>

### 2. Modelagem 

#### Acesso a API do Spotify

Para criarmos nossa aplicação utilizando o serviço de música do Spotify precisamos inicialmente de uma conta no [spotify.com](www.spotify.com) . As mesmas credenciais nos permitem configurarmos a conta de desenvolvedor no serviço [Spotify for Developers](https://developer.spotify.com/). A partir daí é possível a criação de uma aplicação utilizando o API do Spotify acessando o servidor e manipulando dados conforme desejemos. 

Criamos a aplicação “Music is Data” e obtemos nosso *Client ID* e *Client Secret*, informações essenciais para acessarmos a API. 

![spotify_devloper](https://user-images.githubusercontent.com/29662327/194144682-a423d586-633b-4033-ab3b-4e65cb95c9cd.PNG)



#### Biblioteca Python Spotipy

Trabalhamos com a linguagem Python e acessamos os dados de músicas do Spotify usando a biblioteca Spotipy. Esta biblioteca leve, suporta todos os recursos da API da Web do Spotify. 

https://spotipy.readthedocs.io 

![spotipy](https://user-images.githubusercontent.com/29662327/194144786-8ee7f854-6b36-4c8a-987a-098d8673b5a4.PNG)

```

!pip install spotipy

```

Importamos a biblioteca Spotipy e importamos SpotifyClientCrendials. Utilizando nosso Client ID e Client Secret estabelecemos a conexão. 

```
import spotipy
from spotipy.oauth2 import SpotifyClientCredentials

```
```
SPOTIPY_CLIENT_ID='16960f7026d64979bf989042a150a0ff'
SPOTIPY_CLIENT_SECRET='ba1a553dd0e8427cae6a7fbacc676f5d'

```
```
auth_manager = SpotifyClientCredentials(client_id=SPOTIPY_CLIENT_ID, client_secret=SPOTIPY_CLIENT_SECRET)
sp = spotipy.Spotify(auth_manager=auth_manager)

```
#### Coletando Dados 

Nosso objetivo inicial é buscar as músicas mais populares da cantora Anitta no sistema do Spotify. Para isso precisamos identificar sua URI, parâmetro utilizado pelo Spotify para identificar artistas, álbuns e faixas. 

```
artist_name = 'anitta' 

```
```
artists = sp.search(q='artist:'+artist_name,type='artist', limit=1)

```
O código acima nos retorna um JSON com diversas informações sobre a artista, incluindo a URI.
```
artist_uri = artists['artists']['items'][0]['uri']
print(artist_uri)
```
Com sua URI requisitamos suas músicas mais populares. O sistema também nos oferece a possibilidade link de acesso a uma prévia de 30 segundos da música e link para capa do álbum.  
```
results = sp.artist_top_tracks(artist_uri)

for track in results['tracks'][:10]:
    print('track    : ' + track['name'])
    if track['preview_url'] is not None:
        print('audio    : ' + track['preview_url'])
    print('cover art: ' + track['album']['images'][0]['url'])
    print()
      
```
Finalmente criamos um DataFrame com as músicas mais populares importando as respectivas características do áudio. 

[Ver código](https://github.com/lcarcos/music-is-data/blob/main/Projeto%20Final%20-%20BI%20Master%20-%20Luis%20Claudio%20Arcos.ipynb)


<div style="page-break-after: always;"></div>

### 3. Resultados 

#### Características do Áudio

A API do Spotify disponibiliza informações importantes sobre as músicas. Ao analisar as principais características da música, o Spotify é capaz de determinar sua semelhança com outras músicas e fazer recomendações com base em como a música soa em comparação com outras. É assim que o Spotify recomenda artistas menores e músicas mais recentes para que os usuários não ouçam apenas músicas populares de artistas maiores.
Para cada faixa em sua plataforma, o Spotify fornece dados para treze recursos de áudio. O [guia do desenvolvedor do Spotify Web API](https://developer.spotify.com/console/get-audio-features-track/) os define da seguinte forma:

>*Danceability*: Descreve como uma faixa é adequada para dançar com base em uma combinação de elementos musicais, incluindo andamento, estabilidade do ritmo, força da batida e regularidade geral.
>
>*Valence*: Descreve a positividade musical transmitida por uma faixa. Faixas com alta valência soam mais positivas (por exemplo, feliz, alegre, eufórica), enquanto faixas com baixa valência soam mais negativas (por exemplo, triste, deprimida, irritada).
>
>*Energy*: Representa uma medida perceptiva de intensidade e atividade. Normalmente, as faixas energéticas parecem rápidas, altas e barulhentas. Por exemplo, o death metal tem alta energia, enquanto um prelúdio de Bach tem uma pontuação baixa na escala.
>
>*Time*: O tempo geral estimado de uma faixa em batidas por minuto (BPM). Na terminologia musical, tempo é a velocidade ou ritmo de uma determinada peça e deriva diretamente da duração média da batida.
>
>*Loudness*: O volume geral de uma faixa em decibéis (dB). Os valores de volume são calculados em média em toda a faixa e são úteis para comparar o volume relativo das faixas.
>
>*Speechiness*: Detecta a presença de palavras faladas em uma faixa. Quanto mais exclusivamente falada a gravação (por exemplo, talk show, audiolivro, poesia), mais próximo de 1,0 o valor do atributo.
>
>*Instrumentalness*: prevê se uma faixa não contém vocais. Os sons “Ooh” e “aah” são tratados como instrumentais neste contexto. Faixas de rap ou de palavras faladas são claramente “vocais”.
>
>*Liveness*: Detecta a presença de uma audiência na gravação. Valores mais altos de vivacidade representam uma probabilidade maior de que a faixa tenha sido executada ao vivo.
>
>*Acousticness*: Uma medida de confiança de 0,0 a 1,0 se a faixa é acústica.
>
>*Key*: A tonalidade geral estimada da faixa. Os inteiros são mapeados para pitchs usando a notação padrão de Pitch Class. Por exemplo. 0 = C, 1 = C♯/D♭, 2 = D, e assim por diante.
>
>*Mode*: Indica a modalidade (maior ou menor) de uma faixa, o tipo de escala da qual seu conteúdo melódico é derivado. Maior é representado por 1 e menor é 0.
>
>*Duration*: A duração da faixa em milissegundos.
>
>*Time Signature*: Uma assinatura de tempo geral estimada de uma faixa. A fórmula de compasso (medidor) é uma convenção de notação para especificar quantas batidas existem em cada compasso (ou medida).


#### Análise de Dados

Em nossa análise trabalharemos com 7 características principais relacionadas à popularidade: *'acousticness', 'danceability', 'energy', 'instrumentalness', 'liveness', 'speechiness'* e *'valence’* .

Focamos inicialmente nas 3 músicas mais populares da artista Anitta, “La Loto”,  "Dançarina" e "Envolver". Criamos um gráfico radar, que possibilita visualizarmos as características do áudio. A partir da API também filtramos a capa do álbum/*single* e uma prévia com 30 segundos do áudio das faixas. 

#### **La Loto**

cover art: ![La Loto](https://i.scdn.co/image/ab67616d0000b2732c4c95e7117b617b3c3c7de1)

audio    : [Prévia de 30 segundos](https://p.scdn.co/mp3-preview/f68791908c9ebdcd4feec24f1824297b5d7070cb?cid=16960f7026d64979bf989042a150a0ff)

A música “La Loto” apresenta o seguinte gráfico: 

![la_loto_anitta](https://user-images.githubusercontent.com/29662327/194650318-218c6068-31a1-4a19-a938-6e500576714d.png)

<div style="page-break-after: always;"></div>

#### **DANÇARINA (feat. Nicky Jam, MC Pedrinho) - Remix**

cover art: ![Dançarina](https://i.scdn.co/image/ab67616d0000b27386ec217718905b9eeb9f712f)

audio    : [Prévia de 30 segundos](https://p.scdn.co/mp3-preview/9e573962771c2d3d07ad3c788fd8dc37d6f5e1a7?cid=16960f7026d64979bf989042a150a0ff)

A música “DANÇARINA" apresenta o seguinte gráfico: 

![dancarina_anitta](https://user-images.githubusercontent.com/29662327/194653141-4b4929be-2ca0-4d5a-ab36-19937f15e192.png)

O gráfico da música “Dançarina” apresenta um “desenho” semelhante destacando as mesmas características da música anterior.  O gráfico abaixo apresenta uma comparação entre as duas músicas:

![la_loto_dancarina_comapracao](https://user-images.githubusercontent.com/29662327/194665857-ec7e4f07-f404-4888-b469-6a568f092e40.PNG)

A comparação demonstra que a música “La Loto” (carcterísticas 1), possui maior valência, ou seja, soa mais positiva, é mais dançante, e mais “energética”, 

<div style="page-break-after: always;"></div>

#### **Envolver**

cover art: ![Envolver](https://i.scdn.co/image/ab67616d0000b27396e2642422ad16661e673fa2)

audio    : [Prévia de 30 segundos](https://p.scdn.co/mp3-preview/784196314fb6965fbe3a326ff543c8dd6e944ab4?cid=16960f7026d64979bf989042a150a0ff)

A música “Envolver" apresenta o seguinte gráfico: 

![envolver_anitta](https://user-images.githubusercontent.com/29662327/194654328-7d33a44b-e029-4425-a22b-5c84b7fdcc77.png)

Comparação entre a música "La Loto" e "Envolver": 

![la_loto_envolver_comapracao](https://user-images.githubusercontent.com/29662327/194661493-200e107f-a6ec-46e6-831b-380aed0f53d7.PNG)

A comparação, como no caso anterior, demonstra que a música “La Loto” (carcterísticas 1), possui maior valência, soa mais positiva, é mais dançante, e mais “energética”, que a música "Envolver".  

Nossa aplicação possibilita a criação de gráficos relacionando determinadas caractéristas do áudio e popularidade. O gráfico a seguir apresenta as 10 músicas mais populares da Anitta na plataforma Spotify, relacionando com a característica *"danceability"*. 

![fiagura1](https://user-images.githubusercontent.com/29662327/194157483-b6a8d83b-5d2a-4d71-9334-a5b58907c26e.png)

O gráfico acima evidencia músicas altamente dançantes como uma característica da artista Anitta. 

O gráfico a seguir apresenta as 10 músicas mais populares da Anitta na plataforma Spotify, relacionando com a característica *"energy"*.

![energy](https://user-images.githubusercontent.com/29662327/194668352-c625ba42-b6dc-4292-8dd6-38f15d3ec0f8.png)

O gráfico a seguir apresenta as 10 músicas mais populares da Anitta na plataforma Spotify, relacionando com a característica *"valence"*.

![valence](https://user-images.githubusercontent.com/29662327/194668414-183466ea-2ff0-4d21-8645-c8b3019d02c5.png)

Como percebemos a partir da análise dos gráficos acima, algumas características são constantes nas músicas da artista Anitta e contribuem para consolidar sua identidade musical. Músicas altamente dançantes, com alto índice de energia, indicando músicas "agitadas". O parâmentro *valence* com altos índices, também é uma das caractéristicas marcantes, indicando músicas alegres, felizes, que soam positivamente. 

<div style="page-break-after: always;"></div>

### 4. Conclusões 

Na era digital, a música é um dado. Conforme apresentado, a recuperação de informações musicais (music information retrieval) é um campo de pesquisa crescente e essencial para serviços de *streaming*, como Spotify.

Maiores estudos são necessários para relacionar diretamente as características do áudio e a popularidade das músicas. Mas analisando a data de lançamento das músicas, fica claro que os lançamentos  mais recentes são também as músicas mais populares.   Diante da forma como o algoritmo do Spotify funciona, e observando a volatilidade  como uma característica da indústria da música, entendemos a preferência atual do mercado pelo lançamento de *singles*.  

A partir de nossa análise foi possível comprovar através de dados algumas percepções intuitivas sobre a artista Anitta. Seu repertório é marcado por músicas dançantes, com poucas características acústicas, mais elementos eletrônicos, músicas “energéticas” ou “agitadas”, que soam positivamente.

Com o desenvolvimento da aplicação utilizando a API da web do Spotify, foi possível entender um pouco mais sobre metadados musicais e a forma como ciência de dados, psicoacústica, processamento de sinais, aprendizado de máquina e inteligência computacional se combinam para a análise e categorização de dados musicais. 

O projeto segue em desenvolvimento explorando as inúmeras possibilidades oferecidas pela API do Spotify. O objetivo é ampliar as possibilidades de análise e criar um web app com uma interface interativa utilizando Streamlit. 

--- Matrícula: 202.190.234 Pontifícia Universidade Católica do Rio de Janeiro Curso de Pós Graduação *Business Intelligence Master*

