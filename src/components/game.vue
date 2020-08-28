<template>
<div class="logo">
<img src="..\assets\image\logo.png" style="margin : 20px">
  </div>
  <div>
    <button @click="randomStart()" class="btn btn-secondary btn-lg mb-2">Start</button>
    <div class="row">
      <div class="col">
        <button @click="randomDamage(1,50)" class="btn btn-danger mb-4" style="margin :10px">Attack</button> 
        <button @click="randomDamageSP(10,100)" class="btn btn-warning mb-4" style="margin :10px">UltimateAttack</button> 
      </div>
    </div>
    <div class="container-fluid">
      <div class="row">
        <div class="col">
          <div class="alert alert-primary" role="alert">Hero : {{randomPlayer}} HP : {{hp1}}</div> 
          <img :src="image1" class="img-fluid" />
        </div>
        <div class="col">
          <div class="alert alert-primary" role="alert">Villains : {{randomVillains}} HP : {{hp2}}</div>
          <img :src="image2" class="img-fluid" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomAttack: "",
      randomSpAttack: "",
      image1: "",
      image2: "",
      hp1: "",
      hp2: "",
      win: "https://cdn3.iconfinder.com/data/icons/halloween-29/64/grave-512.png", 
      lose: "https://cdn3.iconfinder.com/data/icons/halloween-29/64/grave-512.png", 
      player: [
        {
          name: "GLACIA", 
          hp: 150, 
          image: "https://cdn.bulbagarden.net/upload/thumb/2/23/471Glaceon.png/600px-471Glaceon.png", 
        },
        {
          name: "JOLTEON",
          hp: 200, 
          image: "https://cdn.bulbagarden.net/upload/thumb/b/bb/135Jolteon.png/600px-135Jolteon.png", 
        },
        {
          name: "NIMFIA", 
          hp: 100, 
          image: "https://assets.primagames.com/media/files/sylveon-pokemon-go.png/PRIMA/resize/618x0", 
          
        },
        {
          name: "Vaporeon", 
          hp: 220, 
          image: "https://cdn.bulbagarden.net/upload/thumb/f/fd/134Vaporeon.png/600px-134Vaporeon.png", 
          
        },
      ],
      randomPlayer: "",
      villains: [
        {
          name: "Flareon", 
          hp: 170, 
          image: "https://cdn.bulbagarden.net/upload/thumb/d/dd/136Flareon.png/600px-136Flareon.png", 
        },
        {
          name: "Espeon", 
          hp: 140, 
          image: "https://cdn.bulbagarden.net/upload/thumb/a/a7/196Espeon.png/600px-196Espeon.png", 
        },
        {
          name: "Umbreon",
          hp: 290, 
          image: "https://cdn.bulbagarden.net/upload/thumb/3/3d/197Umbreon.png/600px-197Umbreon.png", 
        },
        {
          name: "Leafeon", 
          hp: 230, 
          image: "https://cdn.bulbagarden.net/upload/thumb/f/f5/470Leafeon.png/600px-470Leafeon.png", 
        },
      ],
      andomVillains: "",
    };
  },

  props: {
    Label: String,
  },

  methods: {
    randomStart: function () {
      var chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[chosenNumber1].name;
      this.hp1 = this.player[chosenNumber1].hp;
      this.image1 = this.player[chosenNumber1].image;

      var chosenNumber2 = Math.floor(Math.random() * this.villains.length);
      this.randomVillains = this.villains[chosenNumber2].name;
      this.hp2 = this.villains[chosenNumber2].hp;
      this.image2 = this.villains[chosenNumber2].image;
    },

    randomDamage: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp1 -= this.randomAttack;
      }
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },

    randomDamageSP: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },
  },
};
</script>

<style>
</style>