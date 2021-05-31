# Aplicação de exemplo usando a **padrão Observer**

O padrão observer pemite que você defina um mecanismo de assinatura para notificar múltiplos objetos
sobre quaisquer eventos que aconteçam com o objeto que eles estão observando.

A aplicação criada, é para monitoramento de clima, que basicamente é composto por 3 componentes:

1- Estação de clima: Um dispositivo físico que obtem os dados do clima atual.

2- O objeto  WeatherData: Pega o dado vindo da estação de clima e atualiza os displays.

3- Display: Mostra para os usuários a atual condições de clima.

O objetivo é criar uma aplicação que usa o objeto WeatherData para atualizaar 3 displays: condições de clima atual, estatisticas de clima e previsão de tempo.

![monitoring weather](/docs/images/monitoring-weather.png)

# Estrutura

1- Usamos a interface chamada geralmente como *"Sujeito"* ou **"Publisher"*. Os objetos usam essa interface para registrar os
observadores e também para remover eles de serem observadores.

```
obs: cada sujeito pode ter muitos observers!
```

2 - Usamos a interface *Observer* para que todo observador em potencial possa implementar essa interface.
Essa interface tem somente um método: update(), que é chamado quando o estado do sujeito é atualizado.

3- Uma classe concreta de sujeito sempre implementa a interface *Sujeito*. Além de conter métodos para registrar ou remover,
a classe concreta também implementa o metodo notifyObserver() que é usado para atualizar todos os observadores atuais.

4- Uma classe concreta observadora pode ser qualquer classe que implementa a inteerface Observer. Cada classe observadora
recebe o valor atual dosujeito através do construtor e atualizado no método update()

Segue abaixo um diagrama de classe da aplicação:

![diagrama de classe](/docs/images/class-diagram.png)

# Prós x Contras do Padrão Observer

- Princípio aberto/fechado. Você pode introduzir novas classes assinantes sem ter que mudar o código da publicadora (e vice versa, caso exista uma interface publicadora).
- Você pode estabelecer relações entre objetos durante a execução.
- Assinantes são notificados em ordem aleatória

# Referências

- [Livro Head First Designer Pattern (Segunda edição)](https://www.amazon.com.br/Head-First-Design-Patterns-Object-Oriented/dp/149207800X/ref=pd_lpo_14_t_0/141-9002804-0455951?_encoding=UTF8&pd_rd_i=149207800X&pd_rd_r=4c8bc77f-fcdc-414a-bc7f-2532902e5165&pd_rd_w=ivF6F&pd_rd_wg=NhHaw&pf_rd_p=cfa1789c-e63b-406f-a502-2b3819ce5a27&pf_rd_r=BCQH9WMS7EK2PSEV5R1P&psc=1&refRID=BCQH9WMS7EK2PSEV5R1P)
- [Refactoring Guru website](https://refactoring.guru/pt-br/design-patterns/observer)