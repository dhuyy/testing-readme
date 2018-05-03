# SCCP Protractor

### Métodos
-----------

`Métodos principais`

| Helper | Descrição |
| ------ | ------ |
| [openMenu](#openmenu) | Abre um item do menu principal. |
| [selectSubmenu](#selectsubmenu) | Seleciona um item do submenu. |
| [isMenuVisible](#ismenuvisible) | Verifica se um item de menu está visível. |

`Login`

| Helper | Descrição |
| ------ | ------ |
| [logInWithUsernameAndPassword](#loginwithusernameandpassword) | Login a partir de um *username* e *password*. |
| [logInWithRole](#loginwithrole) | Login a partir de um *role*. |
| [logOut](#logout) | Logout do sistema. |

`Sales`

| Helper | Descrição |
| ------ | ------ |
| [disableHelpModalIfVisible](#disablehelpmodalifvisible) | Desabilita o *modal* de ajuda. |

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

#### ```isMenuVisible```
Este método verifica se um item de menu está visível.

*Obs.: Este método deve ser invocado dentro de um expect().*

```javascript
expect(sccpE2E.isMenuVisible('registers')).toEqual(true); // PASS - Se o menu estiver visível

expect(sccpE2E.isMenuVisible('registers')).toEqual(false); // FAIL - Se o menu não estiver visível
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

#### ```disableHelpModalIfVisible```
Este método desabilita a opção "Mostrar ao abrir" e fecha o *modal* de ajuda na
tela de *Sales > Data Forecast*.

*Obs.: Este método só precisa ser invocado uma vez para que o modal não apareça mais.*

```javascript
sccpE2E.openMenu('sales');
sccpE2E.selectSubmenu('dataForecast');

// O método abaixo irá desabilitar e fechar o modal de ajuda

sccpE2E.disableHelpModalIfVisible();
```
