## Sobre
Tutorial sobre como usar um pendrive para compartilhar modificações em projetos Git quando o GitHub esta fora do ar ou quando se está sem internet.

## Requisitos
- Sistema operacional Linux
- Python 3

## Passo a passo

### Disponibilizando o pendrive
- Plugar um pendrive na USB do seu computador. 
**Obs:** No diretório /media será criada uma pasta representando o pendrive

- No diretório do projeto digite
```
$ git clone --bare . /media/<nome-da-pasta-do-pendrive>/projeto.git

Obs: Vai criar um clone do projeto no pendrive
```

- Torne o pendrive como origin
```
$ git remote add origin /media/<nome-da-pasta-do-pendrive>/projeto.git
```  

- Enviar as alterações para o pendrive
```
$ git push -u origin master
```

- Agora é só enviar o pendrive para uma outra pessoa para que ela possa fazer 'pull'


### Disponibilizando o pendrive via web server

- No diretório .git no pendrive
```
$ git --bare update-server-info
$ mv hooks/post-update.sample hooks/post-update
```
**Obs:** Isto deixa o pendrive pronto para ser integrado a um servidor web qualquer

- Subir um web server disponível no python
```
$ python3 -m http.server 8000
```
  
- Ir para /tmp ou qualquer outro diretório e digitar
```
  $ git clone https://localhost:8000 <nome-projeto>
```

## Licença
Este projeto está sob licença do MIT. Para mais detalhes, ver o arquivo LICENSE.
