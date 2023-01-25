# Typescript
## Instalação do Node.js

Para instalar o Node.js basta entrar em [https://nodejs.org](https://nodejs.org/), baixar e instalar a versão LTS. Pode ser interessante utilizar algum gerenciador de versões como o **nvm** - para mais informações acesse [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm).

## Inicialização do Projeto

Para inicializar um projeto Node.js, execute o comando no terminal:  `npm init -y`. 
O arquivo **package.json** será criado. Nele ficam as dependências e também os scripts de execução tanto do TypeScript quanto dos testes.

## Instalação e Inicialização do TypeScript

Instale o TypeScript utilizando o comando abaixo, aproveitando para instalar outras dependências:
`npm install typescript jest @types/jest ts-node ts-jest`

Depois disso, crie o arquivo **tsconfig.json**:
`npx tsc --init`

Com isso, o arquivo **tsconfig.js** deve ter sido criado e estamos prontos para começar.

## Configuração do Jest

Configure o Jest utilizando o comando abaixo:
`npx ts-jest config:init`

## Configuração do TypeScript

O TypeScript tem um compilador que faz a conversão do código para JavaScript. Por conta disso, precisamos definir alguns poucos parâmetros:

**tsconfig.json**
```json
{
    "compilerOptions": {
        "incremental": true,
        "target": "es2016",
        "module": "commonjs",
        "outDir": "./dist",
        "strict": true,
        "esModuleInterop": true
    },
    "include": [
        "src",
        "test"
    ]
}
```

## Testando se tudo deu certo

Crie uma pasta chamada **src** e **tests** dentro delas crie dois arquivos:

**src/Circle.ts**  
```javascript
export default class Circle {

   constructor (readonly radius: number) {
   }

    getArea() : number {
        return 2 * Math.PI * this.radius;
    }
}
```

**tests/Circle.test.ts**
```javascript
import Circle from "../src/Circle";

test("Should calculate the area of circle", function () {
    const circle = new Circle(2);
    expect(circle.getArea()).toBe(12.566370614359172);
});
```

Agora basta executar:  `npx jest`.
Se os testes tiverem sido executados com sucesso está **tudo pronto**!