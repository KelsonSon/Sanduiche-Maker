<template>
    <form @submit.prevent="adicionarSanduiche()">
      <fieldset>
        <legend>MONTE SEU SANDUÍCHE</legend>
        <label>
          Pão:
          <select v-model="sanduiche.pao">
            <option disabled value="">Selecione</option>
            <option value="branco">3 Queijos</option>
            <option value="integral">Integral</option>
            <option value="Italiano">Italiano</option>
          </select>
        </label>
        <label>
          Carne:
          <select v-model="sanduiche.carne">
            <option disabled value="">Selecione</option>
            <option value="frango">Frango</option>
            <option value="carne">Carne</option>
            <option value="peixe">Peixe</option>
            <option value="frangoXadrez">Frango Xadrez</option>
          </select>
        </label>
        <label>
            Adicionais:
            <div v-for="item in adicionais" :key="item">
                <input type="checkbox" :value="item" v-model="sanduiche.adicionais">
                {{ item }}
            </div>
        </label>

        <label>
          Salada:
            <div v-for="item in salada" :key="item">
                <input type="checkbox" :value="item" v-model="sanduiche.salada">
                {{ item }}
            </div>
        </label>
        <label>
          Molhos:
          <div v-for="item in molhos" :key="item">
            <input type="checkbox" :value="item" v-model="sanduiche.molho">
            {{ item }}
          </div>
        </label>
        <br>
        <button type="submit">Adicionar sanduíche</button>
      </fieldset>
    </form>
  </template>
  
  <script>
  export default {
    name: 'SandForm',
    data() {
      return {
        sanduiche: {
          pao: '',
          carne: '',
          adicionais: [],
          salada: [],
          molho: []
        },
        adicionais: ['Queijo Cheddar', 'Queijo Suiço', 'Presunto', 'Bacon'],
        salada: ['Alface', 'Tomate', 'Cebola', 'Picles'],
        molhos: ['Maionese', 'Mostarda', 'Ketchup', 'Barbeccue', 'Mostarda e Mel']
      };
    },
    methods: {
      adicionarSanduiche() {
        this.$emit('sanduiche-adicionado', this.sanduiche);
        this.sanduiche = {
          pao: '',
          carne: '',
          adicionais: [],
          salada: [],
          molho: []
        };
      }
    }
  };
  </script>
  <style scoped>
    
    fieldset{
        display: flex;
        flex-direction: column;
        border: 3px solid var(--tertiary-color);
        border-radius: 5px;
        margin: 10px;
        padding: 10px;
        align-items: center;
        justify-content: center;
        height: 100%;
    }
    form{
      width: 100%;
      height: 90vh;
      color: var(--white-color);
    }
    legend{
        font-size: 25px;
        text-align: center;
        font-weight: bold;
        padding: 10px;
        color: var(--secondary-color);
    }
    label{
        padding: 10px;
        font-weight: bold;
        font-size: 18px;
    }
    button[type = 'submit']{
      padding: 5px;
      font-size: 18px;
      border-radius: 5px;
      background: var(--tertiary-color);
      color: var(--white-color);
    }
    button[type = 'submit']:hover{
      cursor: pointer;
      background-color: var(--white-color);
      color: var(--tertiary-color);
    }
    
    select{
        border: 2px solid var(--black-color);
        padding: 2px 5px;
    }
    @media (max-width: 720px){
      form{
        height: 85vh;
        margin-bottom: 20px;
      }
      label{
        padding: 5px;
      }
    }
   
  </style>
  