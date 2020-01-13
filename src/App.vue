<template>
  <div id="app">

    <div class="calculator">
      <div class="calculator__container">
        <div class="calculator__left">
          <h1 class="calculator__title">Сколько стоит разработка веб-сайта?</h1>
          <h3 class="calculator__description">Мы создали интерактивный калькулятор стоимости веб-сайтов, который позволяет легко
            рассчитать приблизительную стоимость разработки. Чтобы максимально точно соответствовать потребностям
            вашего бизнеса, калькулятор предоставляет возможность выбора разных комбинаций функций.</h3>
          <div class="features__title">Дополнительно</div>
          <div class="features__list">
            <button class="features__button" v-on:click="calc(item)" v-bind:class=" { active: item.active } "
                    v-for="item in items">{{ item.name }}
            </button>
          </div>
        </div>
       <div class="calculator__right">
         <div class="calc__wrapper">
           <div class="calc-card">
             <h3 class="calc-card__title">
               Общая стоимость
             </h3>
             <div class="calc-card__total">
               $ <span>{{ result }}</span>
             </div>
             <ul class="calc-card__list">
               <li class="calc-card__item"> <div class="card__item-title">Backend</div> $ {{ totalBackend }}</li>
               <li class="calc-card__item"> <div class="card__item-title">Frontend</div> $ {{ totalFrontend }}</li>
             </ul>
           </div>
         </div>
       </div>
      </div>
    </div>


  </div>
</template>

<script>
  export default {
    name: 'app',
    data() {
      return {
        items: [
          {
            name: 'E-mail login',
            active: false,
            price: 700,
            backendPrice: 400,
            frontendPrice: 300,
          },
          {
            name: 'Social',
            active: false,
            price: 300,
            backendPrice: 100,
            frontendPrice: 200,
          },
          {
            name: 'Search',
            active: false,
            price: 650,
            backendPrice: 400,
            frontendPrice: 200,
          },
          {
            name: 'Maps',
            active: false,
            price: 200,
            backendPrice: 100,
            frontendPrice: 100,
          },
          {
            name: 'Dashboard',
            active: false,
            price: 500,
            backendPrice: 250,
            frontendPrice: 250,
          }
        ],
        result: 0,
        totalBackend: 0,
        totalFrontend: 0,

      }
    },
    methods: {
      calc: function (obj) {
        obj.active = !obj.active;
        this.result = 0;
        this.totalFrontend = 0;
        this.totalBackend = 0;
        const filteredArr = this.items.filter(el => el.active);
        filteredArr.forEach((item) => this.result += item.price);
        filteredArr.forEach((item) => this.totalFrontend += item.frontendPrice);
        filteredArr.forEach((item) => this.totalBackend += item.backendPrice);
      },
    }
  }
</script>

<style lang="scss">
  *{
    margin: 0;
    padding: 0;
  }
  h1 {
    margin: 0;
  }

  .calculator {
    margin-top: 50px;
    &__container {
      display: flex;
      margin: auto;
      max-width: 1024px;
      padding: 0 20px;
    }
    &__left {
      width: 60%
    }
    &__right {

    }
    &__title {
      font-family: Arial, sans-serif;
      font-weight: 900;
      font-size: 70px;
      color: #040918;
      line-height: 70px;
      margin-bottom: 20px;
    }
    &__description {
      max-width: 500px;
      font-weight: 400;
      font-size: 16px;
      color: #111b39;
      margin-bottom: 40px;
      line-height: 23px;
    }
  }
  .features {
    &__title {
      font-family: Arial, sans-serif;
      font-weight: 900;
      font-size: 22px;
      color: #111b39;
      margin-bottom: 20px;
    }
    &__list{
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
    }
    &__button {
      outline: none;
      margin-bottom: 5px;
      cursor: pointer;
      border-radius: 32px;
      border: 1px solid #d9dce5 ;
      font-size: 16px;
      padding: 8px 32px;
      background-color: #fff;
      position: relative;
    }
  }
  .active {
    background-color: #2b55db;
    color: #fff;
    &::after {
      position: absolute;
      left: 18px;
      top: 10px;
      content: '';
      width: 3px;
      height: 9px;
      border: solid white;
      border-width: 0 2px 2px 0;
      transform: rotate(45deg);
    }

  }
  .calc-card {
    width: 300px;
    padding: 0 32px 40px;
    background: #2b55db;
    color: #fff;
    border-radius: 4px;
    &__title {
      padding-top: 40px;
      font-weight: 900;
      font-family: Arial, sans-serif;
      font-size: 24px;
      line-height: 26px;

    }
    &__total {
      font-weight: 900;
      font-family: Arial, sans-serif;
      font-size: 40px;
      line-height: 26px;
      margin: 20px 0;
    }
    &__list {
      list-style: none;
    }
    &__item {
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      font-weight: 400;
      font-size: 18px;
      line-height: 16px;
    }
  }
</style>
