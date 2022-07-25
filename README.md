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

Posso renderizar váriaveis usando o `{{valor da váriavel}}`

## Classes de serviços e injeção de dependências 

ng g s nome_servico Criando um serviço

Na classe de serviço é onde eu mantenho dados de negócio, como uma chamada HTTP, para abstrair a lógica do componente, deixando apenas coisas simples.

Para usar o service, primeiramente no módulo que será usado, eu devo passar uma propriedade providers e deixar claro quem é o provider, no nosso caso, o serviço.

Depois na lógica do componente, no construtor, eu especifico o meu serviço, seguindo esta lógica:
    `constructor(private nameOfService : NameService)`

Feito isto, consigo usar os métodos e váriaveis contidas no serviço Criando

## Interpolação e Property Binding

sdasd 