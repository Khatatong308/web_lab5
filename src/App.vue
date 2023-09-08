<script setup>
</script>


<template>
  <h1>เกม ค้อน กระดาษ กรรไกร ความรัก </h1>
  <div class="con">
    <div>
    <img :src="jojo" />
    <img class ="tab" :src="kojo" />
  </div>
   <div id="app">
        <div class="choices">
            <button @click="play()">เป่ายิ้งชุบ</button>
      </div>
          <div class="result">
            <p v-if="result">{{ result }}</p>
        </div>
        <div class="score">
          <br>
            <p>คะแนนของคุณ: {{ playerScore }}   คะแนนของคอมพิวเตอร์: {{ computerScore }}</p>
        </div>
        <button @click="resetGame">เริ่มเกมใหม่</button>

        <button @click="reset()"> รีรูป</button>
        
       

          </div>
  </div>
  
    
</template>
<script>
       export default {
  data() {
    return {
      result: '',
      playerScore: 0,
      computerScore: 0,
    };
  },
  methods: {  


    
    play() {
      const choices = ['ค้อน', 'กระดาษ', 'กรรไกร','ความรัก'];
      const computerChoice = choices[Math.floor(Math.random() * 4)];
      const userChoice = choices[Math.floor(Math.random() * 4)];
       this.jojo = `${userChoice}.jpg`;
      this.kojo = `${computerChoice}.jpg`;

      

      if (userChoice === computerChoice) {
        this.result = 'เสมอ!';
      } else if (
        (userChoice === 'ค้อน' && computerChoice === 'กรรไกร') ||
        (userChoice === 'กระดาษ' && computerChoice === 'ค้อน') ||
        (userChoice === 'กรรไกร' && computerChoice === 'กระดาษ')||
        (userChoice === 'ความรัก' && computerChoice !== 'ความรัก')
      ) {
        this.result = 'คุณชนะ!';
        this.playerScore++;
      } else {
        this.result = 'คอมพิวเตอร์ชนะ!';
        this.computerScore++;
      }
    },
    resetGame() {
      this.result = '';
      this.playerScore = 0;
      this.computerScore = 0;

 
      
    },reset() {
      window.location.reload();
}
  },
};
     
</script>





<style>
</style>


