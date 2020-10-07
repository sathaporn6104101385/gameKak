<template>
  <div class="container shadow">
    <div>
      <br />
      <h1 class="text-center mb-3 colorf" style="font-size:20px;">
        <b>Infinity War Game</b>
      </h1>
      <div class="container">
        <div class="row mb-3 text-center colorf">
          <div class="col">
            <p>Hero : {{ hero.name }}</p>
            <p>
              <img :src="hero.image" height="100px" class="img-fluid high" />
            </p>
            <div>
              <section id="heroHealth">
                <div
                  id="heroHealth"
                  style="background-color: green; width: 100%;text-align: center;color: #fff;"
                  :style="{ width: hero.hp + '%' }"
                >
                  {{ hero.hp + "%" }}
                </div>
              </section>
            </div>
          </div>
          <div class="col">
            <p style="font-size: 30px; margin-top: 50px;">VS</p>
          </div>
          <div class="col">
            <p>Monster : {{ mon.name }}</p>
            <p><img :src="mon.image" class="img-fluid high" /></p>
            <div>
              <section id="monsterHealth">
                <div
                  id="monsterHealth"
                  style="background-color: green;width: 100%;text-align: center;color: #fff;"
                  :style="{ width: mon.hp + '%' }"
                >
                  {{ mon.hp + "%" }}
                </div>
              </section>
            </div>
          </div>
        </div>
      </div>
      <br />
      <div class="text-center mb-5">
        <button class="btn  btn-outline-danger cf" @click="start">
          START
        </button>
        <button class="btn  btn-outline-primary cf" @click="attack">
          ATTACK
        </button>
        <button class="btn  btn-outline-success cf" @click="SpecialAttack">
          Special Attack
        </button>
        <button class="btn  btn-outline-warning cf" @click="reloadPage">
          Restart
        </button>
      </div>
      <hr style="border: 1px solid red;" />
    </div>
    <div class="text-center">
      <p class="mb-2 colorf" style="font-size:20px;"><b>[คู่มือการเล่น]</b></p>
      <p class="colorf">
        -ตัวละคร Hero : Anakin Skywalker, Iron man, Doraemon <br />
        -ตัวละคร Monster : Thanos, Darth vader, Cell <br />
        -ตัวละครแต่ละตัวมีค่า Health ไม่เท่ากัน <br />
        -กดปุ่ม start เพื่อ randon hero , monster <br />
        -กดปุ่ม attack เพื่อ random การโจมตี <br />
        -กดปุ่ม special attack เพื่อ random การโจมตีพิเศษ <br />
        -กดปุ่ม restart เพื่อ เล่นใหม่อีกครั้ง
      </p>
    </div>
    <br />
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      player: [
        {
          name: "Anakin Skywalke",
          hp: 100,
          image: [require("../assets/AnakinSkywalke.png")],
        },
        {
          name: "Iron man",
          hp: 101,
          image: [require("../assets/ironman.png")],
        },
        {
          name: "Doraemon",
          hp: 104,
          image: [require("../assets/doramon.png")],
        },
      ],

      monster: [
        { name: "Thanos", hp: 101, image: [require("../assets/thanod.png")] },
        {
          name: "Darth vader",
          hp: 102,
          image: [require("../assets/Darthvader.png")],
        },
        {
          name: "Cell (DB)",
          hp: 105,
          image: [require("../assets/call.png")],
        },
      ],
      hero: "",
      mon: "",
      hmax: "",
      mmax: "",
    };
  },
  methods: {
    randomDamage: function(min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function() {
      this.hero = this.player[this.randomDamage(1, 3) - 1];
      this.mon = this.monster[this.randomDamage(1, 3) - 1];
    },
    attack: function() {
      this.hmax = Math.floor(Math.random() * 3 + 10);
      this.hero.hp = this.hero.hp - this.hmax;

      this.mmax = Math.floor(Math.random() * 3 + 10);
      this.mon.hp = this.mon.hp - this.mmax;
      if (this.hero.hp <= 0) {
        this.hero.hp = "";
        alert("MONSTER WIN! END GAME! หากต้องการเล่นอีกครั้งกดปุ่ม Restart.");
        this.end = true;
      } else if (this.mon.hp <= 0) {
        this.mon.hp = "";
        alert("HERO WIN! END GAME! หากต้องการเล่นอีกครั้งกดปุ่ม Restart.");
        this.end = true;
      }
    },
    SpecialAttack: function() {
      this.hmax = Math.floor(Math.random() * 5 + 10);
      this.hero.hp = this.hero.hp - this.hmax;
      this.mmax = Math.floor(Math.random() * 10 + 20);
      this.mon.hp = this.mon.hp - this.mmax;
      if (this.hero.hp <= 0) {
        this.hero.hp = "";
        alert("MONSTER WIN! END GAME! หากต้องการเล่นอีกครั้งกดปุ่ม Restart.");
        this.end = true;
      } else if (this.mon.hp <= 0) {
        this.mon.hp = "";
        alert("HERO WIN! END GAME! หากต้องการเล่นอีกครั้งกดปุ่ม Restart.");
        this.end = true;
      }
    },
    reloadPage() {
      window.location.reload();
    },
  },
};
</script>

<style>
.colorf {
  color: aquamarine;
  font-size: 16px;
}
#monsterHealth {
  width: 100%;
  height: 15px;
  background-color: #eee;
  transition: 0.5s all;
  border-radius: 10px;
}
#heroHealth {
  width: 100%;
  height: 15px;
  background-color: #eee;
  transition: 0.5s all;
  border-radius: 10px;
}
.high {
  height: 100px;
}
.cf {
  font-size: 10px;
}
</style>
