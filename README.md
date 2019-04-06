# EasyBash
Script para rodar atualizações e limpeza de disco no GNU/Linux automaticamente.

#### Descrição
A função do script é fazer o processo de atualização do sistema com limpeza de arquivos temporários e lixos, sem dar muitos comandos.

#### Comandos usados
    apt
    du
    uname
    
## Configuração
### Passo a passo para configurar o script.

## 1 - Criar o script executável na pasta de usuário:
Lembrando que pra rodar o script, é bom deixar ele na pasta __/home/usuario__
```bash
$ gedit exec.run
```
## 2 º - Adicionar o código abaixo:
Copie e cole o código abaixo no seu arquivo criado e save na pasta de usuário: __/home/usuario__
```bash
echo 'Dados do sistema:'
uname -a

echo 'Atualizando os pacotes do sistema:'
apt-get update

echo 'Atualizando o sistema:'
apt-get upgrade -y

echo 'Limpando o sistema de arquivos temporários e desnecessários'

echo 'Espaço que os arquivos de pacotes .deb estavam ocupando:'
du -sh /var/cache/apt/archives

## AUTOREMOVE - remover pacotes que foram instalados automaticamente para satisfazer dependências de outros pacotes e que já não são mais necessários.

apt-get autoremove -y

## AUTOCLEAN - Limpa o seu repositório local — removendo os arquivos de pacotes (.deb) que não podem mais ser baixados (versões antigas) e são completamente inúteis e obsoletos.

apt-get autoclean -y

## CLEAN -  Limpando e removendo todos os arquivos .deb (pacotes) contidos nos diretórios — exceto o lock file.

apt-get clean -y

echo 'Limpeza realizada com sucesso!'

echo 'Espaço que os arquivos de pacotes .deb estão ocupando:'
du -sh /var/cache/apt/archives

```
## 3º - Dar privilégios ao script: 
Importande para poder remover os arquivos temporários e lixo do sistema após atualizações.
```bash
$ chmod +x exec.run
```

## 4º - Executar o script:
Sempre que abrir o terminal, ele já estará na pasta raíz, então, basta executar com privilégios de administrador (sudo):
```bash
$ ./exec.run
```

## 5º - Criando um alias para chamar o script com comando:
Com isso, vamos criar um comando no bash para sempre que quisermos excecutarmos o script de qualquer lugar do terminal, para isso basta seguir os seguintes passos:
```bash
$ gedit /home/usuario/.bashrc
```
Ao executar o comando acima, insira no final do arquivo aberto a sehuinte linha:<br>
__alias easybash='sudo sh /home/usuario/exec.run'__<br>
Pronto, agora sempre que precisar chamar o script basta digitar no terminal o comando __easybash__

# Desenvolvido por<br>
Nome: Mário de Araújo Carvalho<br> 
E-mail: mariodearaujocarvalho@gmail.com<br>
GitHub: https://github.com/MarioDeAraujoCarvalho<br>
Título: EasyBash
<br>

# Licença Apache 2.0

``` 
        Copyright 2017 Mário de Araújo Carvalho
 
  Licensed under the Apache License, Version 2.0 (the "License");
  you may not use this file except in compliance with the License.
  You may obtain a copy of the License at
 
      http://www.apache.org/licenses/LICENSE-2.0
 
  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.

```

<a href="https://www.apache.org/licenses/LICENSE-2.0" target="_blank">Mais detalhes sobre a licença</a>

# Referência
<a href="https://www.diolinux.com.br/2019/01/comando-du-no-linux-espaco-disco.html?m=1" target="_blank">Comando DU no Linux - Como ver o tamanho de arquivos e diretórios pelo terminal</a>
