<template>
  <section class="container  margenTop">
    
        <article class="offset-0 offset-md-3 offset-lg-4 col-12 col-md-6 
            col-lg-4 sombra bgCalculadora">

            <article class="row mb-3 paddingTop">
                    <article class="offset-1 col-10 text-end pantalla">
                        <p class="display-3">{{ getResult }}</p>
                        <p class="display-6">{{ getOperation }}</p>
                    </article>
            </article>

            <!--Primera Fila-->
            <article class="row ">
                    <article class="offset-2 d-grid col-4">
                        <button class="btn btn-warning btn-lg sombra btnAC" @click="clickAC()">AC</button>
                    </article>

                    <article class="d-grid col-2 ">
                        <button class="btn btn-secondary btn-lg sombra btnOperadores" @click="click('÷')">÷</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-danger btn-lg sombra btnDEL" @click="clickDel()">Del</button>
                    </article>
            </article>

            <!--Segunda Fila-->
            <article class="row">
                    <article class="offset-2 d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click="click('7')">7</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click="click('8')">8</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click="click('9')">9</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-secondary btn-lg sombra btnOperadores" @click="click('x')">x</button>
                    </article>
            </article>

            <!--Tercera Fila-->
            <article class="row">
                    <article class="offset-2 d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click= "click('4')">4</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click="click('5')">5</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click="click('6')">6</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-secondary btn-lg sombra btnOperadores" @click="click('-')">-</button>
                    </article>
            </article>

            <!--Cuarta Fila-->
            <article class="row">
                    <article class="offset-2 d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click="click('1')">1</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click="click('2')">2</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click="click('3')">3</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-secondary btn-lg sombra btnOperadores" @click="click('+')">+</button>
                    </article>
            </article>

            <!--Cuarta Fila-->
            <article class="row margenBottom paddingBottom">
                    <article class="offset-2 d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra" @click= "click('.')">.</button>
                    </article>

                    <article class="d-grid col-2">
                        <button class="btn btn-dark btn-lg sombra " @click="click('0')">0</button>
                    </article>

                    <article class="d-grid col-4">
                        <button class="btn btn-secondary btn-lg sombra btnOperadores" @click="clickResult()">=</button>
                    </article>
            </article>
        </article>
  </section>
</template>


<script>
  export default {
    data() {
      return {
        getOperation: "0",
        getResult: "0",
      };
    },

    methods: {
      clickAC() {
        this.getResult = "0";
        this.getOperation = "0";
      },

      clickDel() {
        if (this.getResult.length > 1) {
          this.getResult = this.getResult.substring(0, this.getResult.length - 1);
        } else {
          this.getResult = "0";
        }
      },

      click(par) {
        if (this.getResult == "0") {
          this.getResult = par;
        } else {
          this.getResult += par;
        }
      },

      clickResult() {
        let operation = this.getResult;
        this.getOperation = operation;

        operation = operation.replace("x", "*");
        operation = operation.replace("÷", "/");
        this.getResult = eval(operation);
      },
    },
  };
</script>

<style scoped>

  button {
    margin-block-end: 10%;
    border-radius: 50px;
  }

  button:hover {
    background-color: rgb(126, 126, 126);
  }

  .sombra {
    -webkit-box-shadow: 0px 0px 57px 10px rgba(0, 0, 0, 0.40);
    -moz-box-shadow: 0px 0px 57px 10px rgba(0, 0, 0, 0.40);
    box-shadow: 0px 0px 57px 10px rgba(0, 0, 0, 0.40);
  }

  .pantalla {
      margin-top: 10px;
      border: 1px solid;
      border-radius: 20px;
      background-color: rgba(159, 163, 105, 0.521);
  }

  .margenBottom {
      margin-bottom: 15px;
  }

  .margenTop {
      margin-top: 3.5rem;
  }

  .bgCalculadora {
      border-radius: 15px;
      background-color: rgb(190, 190, 190);
  }

  .paddingTop {
    padding-top: 2rem;
  }

  .paddingBottom {
    padding-bottom: 1.6rem;
  }
  .btnAC:hover {
      background-color: rgb(252, 200, 122);
      border: 1px solid;
  }

  .btnDEL:hover {
      background-color: rgb(255, 89, 89);
      border: 1px solid;
  }

  .btnOperadores:hover {
    background-color: rgb(151, 151, 151);
    border: 1px solid;
  }
</style>
