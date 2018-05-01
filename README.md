# SCCP Protractor

### Métodos
-----------

`Métodos principais`

| Helper | Descrição |
| ------ | ------ |
| [openMenu](#openmenu) | Abre um item do menu principal. |
| [selectSubmenu](#selectsubmenu) | Seleciona um item do submenu. |

`Login`

| Helper | Descrição |
| ------ | ------ |
| [logInWithUsernameAndPassword](#loginwithusernameandpassword) | Login a partir de um *username* e *password*. |
| [logInWithRole](#loginwithrole) | Login a partir de um *role*. |
| [logOut](#logout) | Logout do sistema. |

&nbsp;

### Documentação
----------------

#### ```openMenu```
Este método abre o *dropdown* de um menu principal. O parâmetro deve ser o
nome do menu em Inglês e em *lowercase*, por exemplo:

Registers = registers

A formatação *Camel Case* se aplica aos casos de nomes com mais de uma
palavra, por exemplo:

Input/Output = inputOutput

```javascript
sccpE2E.openMenu('registers');
```

#### ```selectSubmenu```
```javascript
sccpE2E.openMenu('registers'); // Necessário para o método abaixo funcionar
sccpE2E.selectSubmenu('periods');
```

#### ```logInWithUsernameAndPassword```
```javascript
sccpE2E.logInWithUsernameAndPassword('sccp', 'venturus2016');
```

#### ```logInWithRole```
```javascript
sccpE2E.logInWithRole('admin'); // Faz login com as credenciais sccp/venturus2016 
```

#### ```logOut```
```javascript
sccpE2E.logOut();
```
