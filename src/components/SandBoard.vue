<template>
 
    <main>
      <div class="top">
        <div class="logo">
          <h2>SandMaker.com</h2>
        </div>
        <nav>
          <ul>
            <li><a href="#">Home</a></li>
            <li><a href="">Sugestões</a></li>
            <li><a href="">Suporte</a></li>
          </ul>
          
        </nav>
      </div>
      <div class="bot">
        <section class="sec-form">
        <SandForm @sanduiche-adicionado="adicionarSanduiche" />
        </section>
        <section class="sec-card">
          <div class="card" v-for="(sanduiche, index) in sanduiches" :key="index">
            <div class="card-title">
                <h1>Sanduiche de {{ sanduiche.carne }} #{{ index + 1 }}</h1>
            </div>
            <div class="card-body">
                
                <h4>Pão: <span>{{ sanduiche.pao }}</span></h4> 
                <h4>Carne: <span>{{ sanduiche.carne }}</span></h4>
                <h4>Adicionais: <span>{{ sanduiche.adicionais.join(', ') }}</span></h4>
                <h4>Salada: <span>{{ sanduiche.salada.join(', ') }}</span></h4>
                <h4>Molhos: <span>{{ sanduiche.molho.join(', ') }}</span></h4>
            </div>
            <div>
              <button class="btn" @click.prevent="deletarSanduiche(sanduiche)">Deletar</button>
            </div>
          </div>
        </section>
      </div>
    </main>
  </template>
  
  <script>
  import SandForm from './SandForm.vue';
  
  export default {
    name: 'SandBoard',
    components: {
      SandForm
    },
    data() {
      return {
        sanduiches: []
      };
    },
    methods: {
      adicionarSanduiche(sanduiche) {
        this.sanduiches.push(sanduiche);
      },
      deletarSanduiche(sanduiche){
        const index = this.sanduiches.indexOf(sanduiche);
        if (index !== -1) {
          this.sanduiches.splice(index, 1);
        }
      }
    }
  };
  </script>

<style scoped>
    *{
      text-decoration: none;
    }
    main{
        display: flex;
        flex-direction: column;
    }
    section{
      margin-top: 30px;
      display: flex;
      width: 50%;
  
    }
    .logo{
      margin: 10px;
      color: var(--white-color);
    }
    .top{
      display: flex;
      width: 100%;
      height: 50px;
      position: absolute;
      top: 0;
      background: linear-gradient(90deg, rgba(85,43,19,1) 0%, rgba(112,62,29,1) 28%, rgba(134,74,37,1) 90%);
    }
    .top nav{
      margin-left: auto;
    }
    .top nav ul{
      display: flex;
      list-style: none;
      
    }
    .top nav ul li{
      margin: 10px 40px;
      
    }
    .top nav ul li a{
      font-size: 18px;
      color: var(--white-color-aa);
      transition: .3s;
    }
    .top nav ul li a:hover{
      color: var(--white-color);
    }
    .bot{
      display: flex;
      width: 100%;
    }

    .sec-card{
      padding-top: 20px;
      max-height: 100vh;
      overflow-y: scroll;
      flex-wrap: wrap;
      
    }
    

    .card{
        background-color: var(--white-color-aa);
        backdrop-filter: blur(10px);
        border: 3px solid var(--tertiary-color);
        border-radius: 5px;
        display: flex;
        flex-direction: column;
        max-height: 200px;
        width: 100%;
        margin: 10px;
        padding: 10px;
        box-shadow: rgba(0, 0, 0, 0.4) 0px 5px 15px;
    }

    .card-title{
      color: var(--black-color);
    }
    .card-body h4{
      color: var(--tertiary-color);
    }
    .card-body h4 span{
      color: var(--black-color);
    }

    button{
      padding: 5px;
      font-size: 18px;
      border-radius: 5px;
      background: var(--tertiary-color);
      color: var(--white-color);
    }
    button:hover{
      cursor: pointer;
      background-color: var(--white-color);
      color: var(--tertiary-color);
    }
    .btn{
      margin-top: 20px;
    }



    @media (max-width: 720px) {
        .bot{
          flex-direction: column;
        }
        section{
          width: 100%;
        }
        .top nav ul{
      
      justify-content: center;
      }
    }
</style>