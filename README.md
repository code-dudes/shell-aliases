# 10X Developer shortcuts 

### Updating
Just download the aliases file again and open a new shell

### Installation
If you don't know how to install/create aliases, copy paste these commands to get set in 10sec

*None: on mac, you might need to replace .bashrc  with .bash_profile*  

**Step-1**  
Download aliases file  
```
curl https://raw.githubusercontent.com/code-dudes/shell-aliases/main/.shell_aliases -o ~/.shell_aliases
```  

**Step-2**  
Check shell type. Run  `echo $SHELL`.  

**Step-3**  
Open shell configuration file using `vi` or `nano` editor  
*For bash*  
`vi ~/.bashrc` 

*For zsh*  
`vi ~/.zshrc`   
In case adding to .zshrc doesn't work, try adding to .profile or .zprofile.

**Step-4**  
Add below command thee profile file. This command sources/loads the aliases file on shell startup  
`source ~/.shell_aliases`

**Step-5**  
Open a new terminal and try the home alias `

OR  

Just copy and paste below code into terminal directly. This  only works for bash and zsh.  
```
echo 'downloading aliases'
shell=`echo $SHELL | rev | cut -d'/' -f1 | rev`

if curl --silent --show-error --fail https://raw.githubusercontent.com/code-dudes/shell-aliases/main/.shell_aliases -o ~/.shell_aliases > /dev/null; then
  if [ $shell == 'bash' ]; then
  	echo 'using bash'
    (ls  ~/.bashrc || echo '.bashrc does not exist') && echo 'source ~/.shell_aliases' >> ~/.bashrc  && echo 'updated profile' 
  elif [ $shell == 'zsh' ]; then
  	echo 'using zsh'
    (ls  ~/.zshrc || echo '.bashrc does not exist') && echo 'source ~/.shell_aliases' >> ~/.zshrc && echo 'updated profile'
  else
  	echo 'not supported, source alias file manually'
  fi
else
  echo 'failed to download aliases'
fi
```
