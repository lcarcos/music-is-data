# Music is Data: Uma introdução à recuperação de informações musicais (MIR) - análise e categorização de dados musicais


#### Aluno: [Luis Claudio Santos Arcos](https://github.com/lcarcos) 

#### Orientadora: [Professora Evelyn Batista](https://github.com/link_do_github)  

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão". 

- Trabalhos relacionados: - [Nome do Trabalho 1](https://link_do_trabalho.com). - [Nome do Trabalho 2](https://link_do_trabalho.com). 


### Resumo 

A recuperação de informações musicais, ou MIR - Music Information Retrieval, é a ciência de analisar e categorizar dados musicais. MIR é um campo de pesquisa crescente, com muitas aplicações no mundo real. Sistemas de recomendação musical são exemplos de aplicação. A plataforma de streaming de música Spotify aplica técnicas de inteligência artificial para análise de áudio e disponibiliza acesso a esses dados através de sua API da Web. Esse trabalho apresenta o desenvolvimento de uma aplicação de análise e categorização de dados musicais utilizando Python e a API da Web do Spotify.

### Abstract 

Music Information Retrieval, or MIR, is the science of analyzing and categorizing musical data. MIR is a growing field of research with many real-world applications. Music recommendation systems are examples of application. A music streaming platform Spotify applies artificial intelligence techniques to audio analysis and provides access to this data through its web API. This work presents the development of an application for analyzing and categorizing musical data using Python and a Spotify web API.

### 1. Introdução 

Provavelmente, você está inscrito em algum tipo de serviço popular de streaming de música. Seja Spotify, Deezer ou Apple Music, você provavelmente já foi exposto a um aplicativo de recuperação de informações musicais. 

A recuperação de informações musicais (music information retrieval) é a ciência de analisar e categorizar dados musicais. Algumas aplicações do MIR estão intimamente relacionadas ao campo da ciência de dados, ao mesmo tempo em que combinam vários campos, como psicoacústica, processamento de sinais, aprendizado de máquina e inteligência computacional. O MIR é um campo de pesquisa crescente, com muitas aplicações no mundo real. Sistemas de recomendação musical são exemplos de aplicação. 

O Spotify é um serviço de música muito popular que aplica técnicas de aprendizagem de máquina para análise de áudio e recuperação de informações musicais.  Felizmente, o Spotify disponibiliza esses dados através de sua API da Web. É possível explorar as características do áudio e analisar detalhadamente as faixas. Características como dançabilidade, energia, valência, tempo e outras:

Humor: Dançabilidade, Valência, Energia, Tempo
Propriedades: Loudness, Speechiness, Instrumentalness
Contexto: vivacidade, acústica
Segmentos, Tatums, Bares, Beats, Pitchs, Timbre e muito mais
 
Algumas dessas características poderiam explicar o porquê de algumas músicas serem mais ou menos populares. Essa análise é especialmente útil para músicos, gravadoras e distribuidores de música, que podem optar por investir recursos limitados (campanhas publicitárias, equipamento de estúdio, etc.) em faixas que provavelmente se tornarão populares.

Através da API é possível requisitar informações ao servidor do Spotify . É possível buscar por faixas, por artistas, álbuns , atributos das músicas, popularidade dos artistas, os diferentes atributos disponíveis nas músicas dos artistas , os maiores sucessos dos artistas. Muitas coisas que podemos coletar utilizando o APi do Spotify

O objetivo desse trabalho é a criação de um sistema de análise e categorização musical baseado no sistema de recomendação do Spotify.

Utilizaremos Python e o API do Spotify para construir uma aplicação de análise de dados, analisando os detalhes das músicas, popularidade, atributos dos audio, qual música é “melhor” que outra sob determinado aspecto e utilizaremos para criar recomendações baseadas em determinadas características.

### 2. Modelagem 

Acesso a API do Spotify

Credenciais de acesso

Para criarmos nossa aplicação utilizando o serviço de música do Spotify precisamos inicialmente de uma conta no spotify.com . As mesmas credenciais nos permitem configurarmos a conta de desenvolvedor no serviço Spotify for Developer. A partir daí é possível a criação de uma aplicação utilizando o API do Spotify acessando o servidor e manipulando dados conforme desejemos. 

https://developer.spotify.com/



Criamos a aplicação “Music is Data” e obtemos nos Client ID e Client Secret, informações essenciais para acessarmos a API. 


Biblioteca Python Spotipy

Trabalhamos com a linguagem Python e acessamos os dados de músicas do Spotify usando a biblioteca Spotipy. Esta biblioteca leve, suporta todos os recursos da API da Web do Spotify. 

https://spotipy.readthedocs.io 




Importamos a biblioteca Spotipy para conectar ao servidor do Spotify através do API e importamos SpotifyClientCrendials e através de nosso Client ID e Client Secret estabelecemos a conexão. 



### 3. Resultados 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin pulvinar nisl vestibulum tortor fringilla, eget imperdiet neque condimentum. Proin vitae augue in nulla vehicula porttitor sit amet quis sapien. Nam rutrum mollis ligula, et semper justo maximus accumsan. Integer scelerisque egestas arcu, ac laoreet odio aliquet at. Sed sed bibendum dolor. Vestibulum commodo sodales erat, ut placerat nulla vulputate eu. In hac habitasse platea dictumst. Cras interdum bibendum sapien a vehicula. Proin feugiat nulla sem. Phasellus consequat tellus a ex aliquet, quis convallis turpis blandit. Quisque auctor condimentum justo vitae pulvinar. Donec in dictum purus. Vivamus vitae aliquam ligula, at suscipit ipsum. Quisque in dolor auctor tortor facilisis maximus. Donec dapibus leo sed tincidunt aliquam. 

### 4. Conclusões 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin pulvinar nisl vestibulum tortor fringilla, eget imperdiet neque condimentum. Proin vitae augue in nulla vehicula porttitor sit amet quis sapien. Nam rutrum mollis ligula, et semper justo maximus accumsan. Integer scelerisque egestas arcu, ac laoreet odio aliquet at. Sed sed bibendum dolor. Vestibulum commodo sodales erat, ut placerat nulla vulputate eu. In hac habitasse platea dictumst. Cras interdum bibendum sapien a vehicula. Proin feugiat nulla sem. Phasellus consequat tellus a ex aliquet, quis convallis turpis blandit. Quisque auctor condimentum justo vitae pulvinar. Donec in dictum purus. Vivamus vitae aliquam ligula, at suscipit ipsum. Quisque in dolor auctor tortor facilisis maximus. Donec dapibus leo sed tincidunt aliquam. 

--- Matrícula: 202.190.234 Pontifícia Universidade Católica do Rio de Janeiro Curso de Pós Graduação *Business Intelligence Master*

