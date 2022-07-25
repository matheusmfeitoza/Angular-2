# Curso de Angular 2 - Loiane Groner

Ferramentas necessárias:
 - Nodejs
 - Typescript
 - Angular/Cli


## Primeiro projeto

#### Hello world

Criando um componente manualmente:
- Criar uma pasta para ele
- informar o nome.component.ts
- Usar o decorator do Component para explicitar as infos.
- Importar o Component do Angular/Core
- [Veja o exemplo](https://www.github.com/matheusmfeitoza)
- Adicionar no app.module o component;
- Usa-lo;

## ngModules

Temos o módulo principal que é responsável pela aplicação, mas podemos ter outros módulos para evitar o crescimento e poluição de forma indevida do módulo principal

Criando um novo módulo:

    ng g m nome_modulo  ( ng generate module nome_modulo)

Com isto, posso criar novos componentes para servir este módulo. Para levar os componentes para outro módulo, devo criar no módulo a propriedade exports e passar lá quais componentes serão exportados. Para usa-los, devo importar o módulo onde desejo usar.


## Templates

Onde é renderizado o meu componente HTML. No Modulo, temos a propriedade templateURL onde é especificado o caminho do arquivo HTML ou também podemos passar apenas a propriedade `template:` passando uma String literals e usando até no máximo 3 linhas de HTML, isto por boas práticas.

Posso renderizar variáveis usando o `{{valor da variável}}`

## Classes de serviços e injeção de dependências 

ng g s nome_servico Criando um serviço

Na classe de serviço é onde eu mantenho dados de negócio, como uma chamada HTTP, para abstrair a lógica do componente, deixando apenas coisas simples.

Para usar o service, primeiramente no módulo que será usado, eu devo passar uma propriedade providers e deixar claro quem é o provider, no nosso caso, o serviço.

Depois na lógica do componente, no construtor, eu especifico o meu serviço, seguindo esta lógica:
    `constructor(private nameOfService : NameService)`

Feito isto, consigo usar os métodos e variáveis contidas no serviço Criando

## Interpolação e Property Binding

Interpolação conforme já visto antes, é o uso dos `{{}}` para renderizar no HTML dados do componente

Tempos também o binding onde em algumas tags HTML podemos passar um `[]` para renderizar ou buscar dados do componente

## Class e Style Binding

Aplicando o binding em classe e Style

Nos exemplos foi usado o Bootstrap para renderizar cores diferentes com base no valor selecionado no select. Segue exemplo do código:

    <form class="mb-3">
      <select title="teste" id="teste" #classe (change)="(0)">
        <option value="alert-success">Sucesso</option>
        <option value="alert-info">Info</option>
        <option value="alert-warning">Alerta</option>
        <option value="alert-danger">Erro</option>
      </select>
    </form>

    <div
      class="alert"
      role="alert"
      [class.alert-success]="classe.value == 'alert-success'"
    >
      ...
    </div>

Para criar uma variável no HTML é usado o `#`, com isto foi gerado a variável classe `#classe` para armazenar o valor do option.

Usando a diretiva de binding foi criado a classe de acordo com value obtido da variável.

Também foi aplicado usando Interpolação

            <div class="alert {{ classe.value }}" role="alert">
                Aplicando a classe com interpolação
             </div>

Com base no valor da variável é definido a classe.

E também é possível realizar o binding para a propriedade Style

        <div
            class="alert alert-danger"
            role="alert"
            [style.display]="classe.value == 'alert-danger' ? 'block' : 'none'">
            Aplicando a classe somente se ela for tipo erro
        </div>

Com base no valor da propriedade é aplicado um `display block` ou `none`

## Event Binding

Capturando eventos HTML e disparando ações conforme necessário

        <button class="btn btn-primary m-3" (click)="handleClick()">
            Contador: {{ cont }}
        </button>

No exemplo acima foi criado o evento de click onde é passado a função handleClick, que a mesma pega o cont e faz um incremento.


    <form>
      <input
        type="text"
        title="text"
        #valor
        (blur)="getInputValue(valor.value)"
      />
      <input type="text" title="text" (keyup)="otherWayToGetValue($event)" />
    </form>
    Valor digitado no input é: {{ valorArmazenadoInput }}

No exemplo acima faço 2 tipos de captura, quando ocorre o foco e no evento de keyup 

## Two-way Data Binding

Podemos fazer o envio dos valores ao mesmo tempo, tanto para o component quando o HTML, com isso podemos usar a diretiva ngModel `[(ngModel)]`, lembrando sempre do bananas in a box ( bananas dentro de uma caixa ).

Quando usamos esta diretiva, temos que ter importado dentro do modulo o FormsControls, para que o mesmo funcione.

    <article>
        <p>Valor digitado: {{ nome }}</p>
        <input type="text" title="title" [(ngModel)]="nome" />
    </article>

## Reusando componentes com input properties

Aqui aprendemos a passar props em componentes e utiliza-los em outros.

    <app-animais
        [animal]="animal"
        [colecaoAnimais]="colectionOfAnimals"
    >
    </app-animais>

No exemplo acima, foi passado 2 props, uma sendo uma string normal e a outra um array.

No componente que iremos receber as props devemos deixar claro o Input, usando o decorator `@Input`:
    
     @Input() animal: string = '';
     @Input() colecaoAnimais = [''];

E depois podemos usa-lo normalmente no HTML:

    <p>Veio do outro component o animal: {{ animal }}</p>

    <p>Renderizando um array de outro component</p>

    <ul>
      <li *ngFor="let animal of colecaoAnimais">{{ animal }}</li>
    </ul>
