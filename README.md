# SCCP Protractor

### Métodos
-----------

`Métodos principais`

| Helper | Descrição |
| ------ | ------ |
| [openMenu](#openmenu) | Abre um item do menu principal. |

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
```javascript
sccp.openMenu('cadastros'); // parâmetro em pt-BR
sccp.openMenu('registers'); // parâmetro em EN
```

#### ```logInWithUsernameAndPassword```
```javascript
sccp.logInWithUsernameAndPassword('sccp', 'venturus2016');
```

#### ```logInWithRole```
```javascript
sccp.logInWithRole('admin'); // Faz login com as credenciais sccp/venturus2016 
```

#### ```logOut```
```javascript
sccp.logOut();
```
