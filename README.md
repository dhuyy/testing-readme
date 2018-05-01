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
exato nome do menu em Inglês e em *lowercase*, por exemplo:

- `Registers = registers`

Para os nomes com mais de uma palavra, deve-se usar *Camel Case*, por exemplo:

- `Input/Output = inputOutput`

```javascript
sccpE2E.openMenu('registers');
sccpE2E.openMenu('inputOutput');
```

#### ```selectSubmenu```
Este método seleciona um submenu após o *dropdown* do menu principal correspondente
for aberto. O parâmetro deve ser o exato nome do submenu em Inglês e em
*lowercase*, por exemplo:

- `Periods = periods`

Para os nomes com mais de uma palavra, deve-se usar *Camel Case*, por exemplo:

- `Setup Kits = setupKits`

- `Semester Forecast = semesterForecast`

Para submenus com nomes idênticos como *Input/Output > Proportional* e
*Simulation > Proportional* deve-se adicionar o nome do menu correspondente
ao início do nome do submenu, por exemplo:

- `Input/Output > Proportional = inputOutputProportional`

- `Simulation > Proportional = simulationProportional`

```javascript
sccpE2E.openMenu('registers'); // Necessário para o método abaixo funcionar
sccpE2E.selectSubmenu('periods');

sccpE2E.openMenu('inputOutput'); // Necessário para o método abaixo funcionar
sccpE2E.selectSubmenu('inputOutputProportional');
```

#### ```logInWithUsernameAndPassword```
Este método preenche os campos de *username* e *password* e clica no botão
para entrar no sistema.

O primeiro parâmetro deve ser o *username* seguido do *password*.

*Obs.: É necessário estar na tela de login para que este método funcione.*

```javascript
sccpE2E.logInWithUsernameAndPassword('sccp', 'venturus2016');

sccpE2E.logInWithUsernameAndPassword('viewer', 'viewer');
```

#### ```logInWithRole```
Este método preenche os campos de *username* e *password* e clica no botão
para entrar no sistema.

O parâmetro deve ser a *role* correspondente ao usuário.

*Obs.: É necessário estar na tela de login para que este método funcione.*

```javascript
sccpE2E.logInWithRole('admin'); // Faz login com as credenciais sccp/venturus2016

sccpE2E.logInWithRole('viewer'); // Faz login com as credenciais viewer/viewer
```

#### ```logOut```
Este método clica no botão de *logout* e sai do sistema.

*Obs.: É necessário estar autenticado para que este método funcione.*

```javascript
sccpE2E.logOut();
```
