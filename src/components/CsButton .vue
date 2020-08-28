<template>
<div>
  <v-button @click="randomStart()" class="btn">
    <img src="https://ioi-game.com/wp-content/uploads/2020/06/PLAY-GAME.png" height="80" width="200"/>
    </v-button>
    <br />
    <button v-bind:disabled="end" @click="randomDamage()" @click.prevent="playSound('https://cdn.discordapp.com/attachments/392353546332405763/748744472472322048/PUNCH.mp3')" class="btn btn-info">Attack{{Label}}</button>
    <button v-bind:disabled="end" @click="randomSpDamage()" @click.prevent="playSound(player[chosenNumber1].spsound)"  class="btn btn-info">Special Attack{{Label}}</button>
    <div class="row text-light">
      <div class="col-sm">
        <p>{{randomPlayer}}</p>
        <p>HP : {{hp1}}</p>
        <p>
          <img v-bind:style="{width : hp1 + 'px'}" :src="healthbar" alt height="100px" />
        </p>
        <img :src="imagePlayer" :height="hp1" />
      </div>

      <div class="col-sm text-danger">
        <h1 v-if="hp1 <= 0 & hp2 <=0">
          <br />
          <img src="https://i.pinimg.com/originals/0d/f1/c0/0df1c0e8aba53aac2afd443534f531ac.gif"/>
          
          
        </h1>
        <h1 v-else-if="hp2 <= 0 ">
          <br />
          <img src="https://media3.giphy.com/media/UQJURGM2x5y8QA4bp9/source.gif">
          {{randomPlayer}} WIN
        </h1>
        <h1 v-else-if="hp1 <= 0 ">
          <br />
          <img src="https://media3.giphy.com/media/UQJURGM2x5y8QA4bp9/source.gif">
          {{randomMonster}} WIN
        </h1>
        <br /><br /><br />
        <p v-if="hp1!=0 & hp2!=0">
          <img
            src="http://www.pngmart.com/files/11/Versus-Battle-PNG-File.png" height="200" weight="200"
          />
        </p>
      </div>
      <div class="col-sm">
        <p>{{randomMonster}}</p>
        <p>HP : {{hp2}}</p>
        <p>
          <img v-bind:style="{width: hp2 + 'px'}" :src="healthbar" alt height="100px" />
        </p>
        <img :src="imageMonster" :height="hp2" />
      </div>
    </div>
  </div>



</template>

<script>
export default {
  data: function () {
    return {
      randomPlayer: "",
      randomMonster: "",
      randomPlayerAttack: "",
      randomMonsterAttack: "",
      chosenNumber1:"",
      chosenNumber2:"",
      imagePlayer: "",
      imageMonster: "",
      hp1: "1",
      hp2: "1",
      end: true,
      healthbar:
           "https://www.tynker.com/projects/images/d7d94ea7a9f71d5422fac64423233b41a1585788/health-bar---red-bar.png", 
      
        player: [
        {
          name: "Snow white",
          hp: 150,
          image1:
            "https://i.pinimg.com/originals/1e/23/77/1e23773811b559adf5e80edf28df8047.gif",
          
        },
        {
          name: "Cinderella",
          hp: 155,
          image1:
            "https://giffiles.alphacoders.com/320/32063.gif",

        },
        {
          name: "Aurora",
          hp: 180,
          image1:
            "https://dl8.glitter-graphics.net/pub/1055/1055258cf14264gpa.gif",
          
        },
        {
          name: "Ariel",
          hp: 170,
          image1:
            "https://i.pinimg.com/originals/de/65/7b/de657b8fd2f188593623fd41901c4731.gif",
          
        },
        {
          name: "Belle ",
          hp: 160,
          image1:
            "https://i.pinimg.com/originals/4a/da/b2/4adab20327ef62b09067c4f29e230ee8.gif",
          
        },
        {
          name: "Jasmine ",
          hp: 190,
          image1:
            "https://m.gifmania.co.uk/Walt-Disney-Animated-Gifs/Animated-Disney-Movies/Aladdin/Princess-Jasmine/Jasmine-85412.gif",
          
        },
      ],
      monster: [
        {
          name: "Elsa",
          hp: 200,
          image1:
            "https://3.bp.blogspot.com/-Gg8YBJLOATA/WDZwFRz2oxI/AAAAAAALbW8/3y9SUjvMio87qfYBPMHVgYE-CkYBOKCpACLcB/s1600/AS000712_10.gif",
        },
        {
          name: "Anna",
          hp: 200,
          image1:
            "https://4.bp.blogspot.com/-I1bdjk1rh1M/WDZwFp8qk3I/AAAAAAALbXA/bqzOpiPoSq4YNMaNzX2Tbnep9jnrfRkUgCLcB/s1600/AS000712_09.gif",
          
        },
        {
          name: "Tinna",
          hp: 170,
          image1:
            "https://3.bp.blogspot.com/-FFQymyBN1Ok/XO8q_iM9yCI/AAAAAAAMj34/NFJSB6mVdCAN4QgHPbws9N1leMC7fleywCLcBGAs/s1600/AS0005332_19.gif?time=Fri%20Aug%2028%202020%2023:01:44%20GMT+0700%20(%E0%B9%80%E0%B8%A7%E0%B8%A5%E0%B8%B2%E0%B8%AD%E0%B8%B4%E0%B8%99%E0%B9%82%E0%B8%94%E0%B8%88%E0%B8%B5%E0%B8%99)",
          
        },
        
      ],
    };
  },
  props: {
    Label: String,
  },

  methods: {
    randomStart: function () {
      this.chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[this.chosenNumber1].name;
      this.hp1 = this.player[this.chosenNumber1].hp;
      this.imagePlayer = this.player[this.chosenNumber1].image1;
      this.chosenNumber2 = Math.floor(Math.random() * this.monster.length);
      this.randomMonster = this.monster[this.chosenNumber2].name;
      this.hp2 = this.monster[this.chosenNumber2].hp;
      this.imageMonster = this.monster[this.chosenNumber2].image1;
      this.end = false;
    },
    randomDamage: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 10) + 1, 3);
      this.hp2 -= this.randomPlayerAttack;
      this.imagePlayer = this.player[this.chosenNumber1].image2;      
      this.randomMonsterAttack = Math.max(Math.floor(Math.random() * 15) + 1,5);
      this.hp1 -= this.randomMonsterAttack;
      this.imageMonster = this.monster[this.chosenNumber2].image2;
      if (this.hp1 <= 0 & this.hp2 <=0) {
        this.hp1 = 0;
        this.hp2 = 0;
        this.end = true;        
      }
      else if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.end = true;
        this.imageMonster = this.monster[this.chosenNumber2].image1;
      }
      else if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.end = true;
        this.imagePlayer = this.player[this.chosenNumber1].image1;
      }
    },
    randomSpDamage: function () {
      this.randomPlayerAttack = Math.max(Math.floor(Math.random() * 20) + 1,10);
      this.hp2 -= this.randomPlayerAttack;
      this.imagePlayer = this.player[this.chosenNumber1].image3;      
      this.randomMonsterAttack = Math.max(Math.floor(Math.random() * 15) + 1,5);
      this.hp1 -= this.randomMonsterAttack;
      this.imageMonster = this.monster[this.chosenNumber2].image2;    
      if (this.hp1 <= 0 & this.hp2 <=0) {
        this.hp1 = 0;
        this.hp2 = 0;
        this.end = true;             
      }
      else if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.end = true;
        this.imageMonster = this.monster[this.chosenNumber2].image1
      }
      else if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.end = true;
        this.imagePlayer = this.player[this.chosenNumber1].image1;
      }
    },
    
  },
};
</script>

<style>
</style>