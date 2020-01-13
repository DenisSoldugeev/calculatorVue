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
           <span class="calc__result">{{ result }}</span>
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
            Frontend: 300,
          },
          {
            name: 'Social',
            active: false,
            price: 300,
            backendPrice: 100,
            Frontend: 200,
          },
          {
            name: 'Search',
            active: false,
            price: 650,
            backendPrice: 400,
            Frontend: 200,
          },
          {
            name: 'Maps',
            active: false,
            price: 200,
            backendPrice: 100,
            Frontend: 100,
          },
          {
            name: 'Dashboard',
            active: false,
            price: 500
          }
        ],
        result: 0,
      }
    },
    methods: {
      calc: function (obj) {
        obj.active = !obj.active;
        this.result = 0;
        const filteredArr = this.items.filter(el => el.active);
        filteredArr.forEach((item) => this.result += item.price);
      },
    }
  }
</script>

<style lang="scss">
  *{
    margin: 0;
    padding: 0;
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

      width: 49%;
    }
    &__right {
      width: 49%;
    }
    &__title {
      font-family: Arial, sans-serif;
      font-weight: 900;
      font-size: 70px;
      color: #040918;
      margin-bottom: 20px;
    }
    &__description {
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
</style>
