## Установка и настройка  

#### Требования к оборудованию
* 2 ГГц или более быстрый процессор или процессор SoC.
* 8 гигабайт (ГБ) для 32-битной или 2 ГБ для 64-битной оперативной памяти.
* 16 ГБ на жестком диске.

### Установка в Linux

#### Установка Git

Для компиляции и запуска демона вам нужно установить gcc и git.
```
sudo apt-get update
sudo apt-get install build-essential git -y
```

#### Установка Go
Это несколько сжатых шагов, которые помогут вам быстро начать работу, но мы рекомендуем выполнить шаги по установке на [https://golang.org/doc/install](https://golang.org/doc/install).

Загрузите Go 1.11 и распакуйте исполняемые файлы:
```
wget https://storage.googleapis.com/golang/go1.11.5.linux-amd64.tar.gz
sudo tar -zxvf  go1.11.5.linux-amd64.tar.gz -C /usr/local/
```

#### Настройка Go

Создайте каталог для хранения всех ваших проектов Go (ниже мы просто поместим каталог в наш домашний каталог, но вы можете использовать любой каталог, который захотите).

```
mkdir $HOME/go
```

Установите этот каталог в качестве вашего пути перехода:

Отредактируйте `.profile` в вашем домашнем каталоге и добавьте следующее в конец файла (если вы использовали другой каталог go, обязательно измените его ниже):

```
echo "export GOPATH=$HOME/go" >> .profile
echo "export PATH=$PATH:/usr/local/go/bin" >> .profile
```

Затем запустите:

```
source ~/.profile
```

Go теперь должен быть установлен.

#### Установка even-go

Загрузить копию источника:
```
go get github.com/evenfound/even-go
```

Он будет использовать git для извлечения исходного кода в `$GOPATH/src/github.com/evenfound/even-go`

Переключитесь на последний релиз:
```
git checkout v0.1.1
```

Примечание: `go get` оставляет репо, указывая на `master` которая является отраслью, используемой для активного развития. Запуск even-go из `master` не рекомендуется. Проверьте [последние релизы](https://github.com/evenfound/even-go/releases) для доступных версий, которые вы используете в оформлении заказа.
Чтобы скомпилировать и запустить исходный код:
```
cd $GOPATH/src/github.com/evenfound/even-go
go run openbazaard.go start
```

Примечание для новичков GOLANG:

В большинстве проектов вы обычно выполняете `git clone` репозитория для того, чтобы начать работу.

С `even-go` нет необходимости вручную `git clone`. проект сам это сделает для вас, когда вы выпускаете команду`go get github.com/evenfound/even-go`, использоввание `git clone` даст вам только хранилище, в котором отсутствует много рекурсивных зависимостей и создадутся лишние головные боли.

Если вы привыкли, что все ваши другие проекты находятся в каком-то другом месте на диске, просто сделайте символическую ссылку из `$GOPATH/src/github.com/evenfound/even-go` в вашу обычную рабочую папку.

Для начала работы и коммитов на свой форк обязательно добавьте свой git remote в `$GOPATH/src/github.com/evenfound/even-go` папка с:

```
cd $GOPATH/src/github.com/evenfound/even-go
git remote add myusername git@github.com:myusername/openbazaar-go.git
```

### MAC OS X install notes

#### Install Git

You need to have Go (and git) installed to compile and run the daemon.

```
brew install git
```

#### Install Go
These are some condensed steps which will get you started quickly, but we recommend following the installation steps at [https://golang.org/doc/install](https://golang.org/doc/install).

Use brew to install Go 1.11:
```
brew install go@1.11
```

Go may also be installed following the directions at [https://golang.org/doc/install](https://golang.org/doc/install).

Note: OpenBazaar has not been tested with v1.11 and may cause problems

#### Setup Go

Create a directory to store all your Go projects (below we just put the directory in our home directory but you can use any directory you want).

```
mkdir $HOME/go
```

Set that directory as your go path:

Edit `.profile` in your home directory and append the following to the end of the file (if you used a different go directory make sure to change it below):
```
echo "export GOPATH=$HOME/go" >> .profile
echo "export PATH=$PATH:/usr/local/go/bin" >> .profile
```

Then run:
```
source ~/.profile
```

Go should now be ready.

#### Install openbazaar-go

Checkout a copy of the source:
```
go get github.com/evenfound/even-go
```

It will use git to checkout the source code into `$GOPATH/src/github.com/evenfound/even-go`

Checkout a release version:
```
git checkout v0.13.3
```

Note: `go get` leaves the repo pointing at `master` which is a branch used for active development. Running OpenBazaar from `master` is NOT recommended. Check the [release versions](https://github.com/evenfound/even-go/releases) for the available versions that you use in checkout.

To compile and run the source:
```
cd $GOPATH/src/github.com/evenfound/even-go
go run openbazaard.go start
```
NOTE: If you have Xcode installed you may get the response `signal: killed`. If you do try running the following instead.

```
go run --ldflags -s openbazaard.go start -t
```

NOTE FOR NEW GOLANG HACKERS: 

In most projects you usually perform a `git clone` of the repository in order to start hacking. 

With `openbazaar-go` There's no need to manually `git clone` the project, this is done for you when you issue the `go get github.com/evenfound/even-go` command, doing a manual `git clone` will only give you a repository that's missing a lot of recursive dependencies and building headaches.

If you are used to having all your other projects in some other place on disk, just make a symlink from `$GOPATH/src/github.com/evenfound/even-go` into your usual workspace folder.

To start hacking make sure to add your git remote into the `$GOPATH/src/github.com/evenfound/even-go` folder with:
```
cd $GOPATH/src/github.com/evenfound/even-go
git remote add myusername git@github.com:myusername/openbazaar-go.git
```
### Windows install notes

#### Install dependencies

You need to have Go, Git, and GCC installed to compile and run the OpenBazaar-Go daemon.

- **Go v1.11**
    + https://golang.org/dl
    + Note: OpenBazaar has not been tested on v1.12 and may cause problems
- **Git**
    + https://git-scm.com/download/win
- **TDM-GCC/MinGW-w64**
    + http://tdm-gcc.tdragon.net/ 
    + A standard installation should automatically add the correct `PATH`, but if it doesn't:
        * Open the command prompt and type: `setx PATH "%PATH;C:\TDM-GCC-64\bin"`

#### Setup Go

Create a directory to store all your Go projects (e.g. `C:\goprojects`):

- Set your GOPATH
    + Open the command prompt and type: `setx GOPATH "C:\goprojects"`

#### Install openbazaar-go

- Install `openbazaar-go`:
    + Open the command prompt and run: `go get github.com/evenfound/even-go`. This will use git to checkout the source code into `%GOPATH%\src\github.com\OpenBazaar\openbazaar-go`.
- Checkout an OpenBazaar release:
    + Run `git checkout v0.13.3` to checkout a release version.
    + Note: `go get` leaves the repo pointing at `master` which is a branch used for active development. Running OpenBazaar from `master` is NOT recommended. Check the [release versions](https://github.com/evenfound/even-go/releases) for the available versions that you use in checkout.
- To compile and run `openbazaar-go`:
    + Open the command prompt and navigate the source directory: `cd %GOPATH%\src\github.com\OpenBazaar\openbazaar-go` 
    + Type: `go run openbazaard.go start`

##### Системные настройки 
* Добавить в системные переменные LIBP2P_FORCE_PNET=1
##### Настройка и запуск ПО 
После установки необходимо установить дефолтные конфигурации . Для этого в командной строке выполните следующую команду

```sh
even-go init --testnet
```
Эта команда создает `~/.openbazaar-testnet`  директорию , и записывает  в ней  дефолтные настройки . Перед тем как запускать программу нужно скачать ключ приватной сети (`swarm.key`)  и переносить  в папку  `~/.openbazaar-testnet`

Программу можно запустить из следующей команды.
```sh
even-go start --testnet
```
