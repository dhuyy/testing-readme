# SCCP Protractor

### Métodos
-----------

`Métodos principais`

| Helper | Descrição |
| ------ | ------ |
| [openWebPage](#openwebpage) | Acessa o endereço *localhost:3000*. |
| [openMenu](#openmenu) | Abre um item do menu principal. |
| [closeMenu](#closemenu) | Fecha um item do menu principal. |
| [selectSubmenu](#selectsubmenu) | Seleciona um item do submenu. |
| [isMenuVisible](#ismenuvisible) | Verifica se um item de menu está visível. |
| [isSubmenuVisible](#issubmenuvisible) | Verifica se um item de submenu está visível. |

`Database`

| Helper | Descrição |
| ------ | ------ |
| [dropDatabase](#dropdatabase) | Requisita uma limpeza do banco de dados ao servidor. |

`Login`

| Helper | Descrição |
| ------ | ------ |
| [logInWithUsernameAndPassword](#loginwithusernameandpassword) | Login a partir de um *username* e *password*. |
| [logInWithRole](#loginwithrole) | Login a partir de um *role*. |
| [logOut](#logout) | Logout do sistema. |

`Registers > Periods`

| Helper | Descrição |
| ------ | ------ |
| [addPeriods](#addperiods) | Cria um determinado número de períodos. |

`Registers > Products`

| Helper | Descrição |
| ------ | ------ |
| [linkSalesPartNumberInProductPage](#linksalespartnumberinproductpage) | Faz a ligação de Part Number de Vendas com um novo Produto. |

`Registers > Customer`

| Helper | Descrição |
| ------ | ------ |
| [linkPartNumberInCustomerPage](#linkpartnumberincustomerpage) | Faz a ligação de Part Number com um novo Cliente. |

`Sales > Forecast Data`

| Helper | Descrição |
| ------ | ------ |
| [disableHelpModalIfVisible](#disablehelpmodalifvisible) | Desabilita o *modal* de ajuda. |

&nbsp;

### Documentação
----------------

<!---
-
- openWebPage
-
-->

#### ```openWebPage```
Este método acessa o endereço http://localhost:3000 na barra de endereços do browser.

*Obs.: Normalmente este método só é invocado dentro de um beforeAll().*

```javascript
beforeAll() {
  sccpE2E.openWebPage();
}
```

<!---
-
- openMenu
-
-->

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

<!---
-
- closeMenu
-
-->

#### ```closeMenu```
*Obs.: Este método tem a mesma lógica do método openMenu() e foi escrito
apenas para dar mais sentido a leitura do código do test case.*

```javascript
sccpE2E.openMenu('registers'); // Abre

sccpE2E.closeMenu('registers'); // Fecha
```

<!---
-
- selectSubmenu
-
-->

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

<!---
-
- isMenuVisible
-
-->

#### ```isMenuVisible```
Este método verifica se um item de menu está visível.

*Obs.: Este método deve ser invocado dentro de um expect().*

```javascript
expect(sccpE2E.isMenuVisible('registers')).toEqual(true); // PASS - Se o menu estiver visível

expect(sccpE2E.isMenuVisible('inputOutput')).toEqual(false); // PASS - Se o menu não estiver visível
```

<!---
-
- isSubmenuVisible
-
-->

#### ```isSubmenuVisible```
Este método verifica se um item de submenu está visível.

*Obs.: Este método deve ser invocado após o método openMenu().*

```javascript
sccpE2E.openMenu('inputOutput'); // Abre o menu Input/Output

expect(sccpE2E.isMenuVisible('analysis')).toEqual(true); // PASS - Se o submenu Analysis estiver visível
```

<!---
-
- dropDatabase
-
-->

#### ```dropDatabase```
Este método faz uma requisição ao servidor para uma total limpeza do banco de dados. O endereço requisitado
é o http://localhost:53993/api/Database/Drop.

É preferível usar esse método dentro de um beforeAll (caso desejar limpar o DB para a *suite*)
ou dentro de um beforeEach (caso desejar limpar o DB para cada *test case*).

*Obs.: Este método põe a execução de comandos do WebDriver em hold até que a requisição HTTP seja resolvida.*

```javascript
// Limpa o DB antes de cada Suite
beforeAll(function() {
  sccpE2E.dropDatabase();
})

// Limpa o DB antes de cada Test Case
beforeEach(function() {
  sccpE2E.dropDatabase();
})
```

<!---
-
- logInWithUsernameAndPassword
-
-->

#### ```logInWithUsernameAndPassword```
Este método preenche os campos de *username* e *password* e clica no botão
para entrar no sistema.

O primeiro parâmetro deve ser o *username* seguido do *password*.

*Obs.: É necessário estar na tela de login para que este método funcione.*

```javascript
sccpE2E.logInWithUsernameAndPassword('sccp', 'venturus2016');

sccpE2E.logInWithUsernameAndPassword('viewer', 'viewer');
```

<!---
-
- logInWithRole
-
-->

#### ```logInWithRole```
Este método preenche os campos de *username* e *password* e clica no botão
para entrar no sistema.

O parâmetro deve ser a *role* correspondente ao usuário.

*Obs.: É necessário estar na tela de login para que este método funcione.*

```javascript
sccpE2E.logInWithRole('admin'); // Faz login com as credenciais sccp/venturus2016

sccpE2E.logInWithRole('viewer'); // Faz login com as credenciais viewer/viewer
```

<!---
-
- logOut
-
-->

#### ```logOut```
Este método clica no botão de *logout* e sai do sistema.

*Obs.: É necessário estar autenticado para que este método funcione.*

```javascript
sccpE2E.logOut();
```

<!---
-
- addPeriods
-
-->

#### ```addPeriods```
Este método cria um determinado número de períodos. A quantidade de períodos
criados é determinado por um número passado como parâmetro. 

```javascript
sccpE2E.addPeriods(); // Cria 1 período

sccpE2E.addPeriods(5); // Cria 5 períodos
```

<!---
-
- linkSalesPartNumberInProductPage
-
-->

#### ```linkSalesPartNumberInProductPage```
Este método faz a ligação de um Part Number de Vendas na hora da criação de um Produto. O método irá
clicar no botão de ligação, selecionar o Part Number de acordo com o parâmetro passado
na chamada e clicar no botão de confirmar a ligação.

```javascript
sccpE2E.linkSalesPartNumberInProductPage('Dell X8237'); // Faz a ligação de um Produto com o PN de Vendas: Dell X8237
```

<!---
-
- linkPartNumberInCustomerPage
-
-->

#### ```linkPartNumberInCustomerPage```
Este método faz a ligação de um Part Number na hora da criação de um Cliente. O método irá
clicar no botão de ligação, selecionar o Part Number de acordo com o parâmetro passado
na chamada e clicar no botão de confirmar a ligação.

```javascript
sccpE2E.linkPartNumberInCustomerPage('Samsung Z0438'); // Faz a ligação de um Cliente com o PN: Samsung Z0438
```

<!---
-
- disableHelpModalIfVisible
-
-->

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
