
# Some personal tiny shell or python scripts. Thanks for your contribution for this repository.



## sayHello is demo for flask , html, css.

```shell
git clone https://github.com/luogeshibu/wow.git
cd sayHello
```

## FlaskMysql is demo for flask and mysql. you should install flask and flask_mysqldb python module.

```shell
git clone https://github.com/luogeshibu/wow.git
cd FlaskMysql
pip install flask flask_mysqldb
python app.py
```
open your browser for http://localhost:5000.

## install OH MY ZSH for any user. you should execute the below command by specifying the user on your Linux server. eg: common user vagrant.

```
sudo apt-get install -y net-tools zsh curl tree git vim
yes | sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
sed -i 's/(git)/(git zsh-autosuggestions  zsh-syntax-highlighting)/g' ./.zshrc
sed -i 's/robbyrussell/aussiegeek/g' ./.zshrc
echo "export EDITOR='vim'" >> ./.zshrc
echo "export VISUAL='vim'" >> ./.zshrc
zsh
```
