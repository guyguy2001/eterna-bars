<template>
  <div>
    <div style="margin: 5px;">
      <div style="margin: 5px;">
        <b>Submissions:</b> <span style="line-height: 1.9em; font-size: 1.5em; font-weight: bold; color: #FEC942;">{{submits}}</span>/4800
        <div class="meter-wrap" style="position:relative; top:15px; left:10px; width: 381.500px;height: 18px; border: 2px solid #467097; display: inline-block;
            border-radius: 5px; background-color:#000F27">
          <div class="rounded-small" style="height: 100%;" :style="{width: levelData.done/(levelData.done + levelData.left) * 100 + '%', 'background-color' : levelData.color}"></div>
          <span style="position: relative; top: -17px;">Level {{levelData.level}} : {{levelData.levelName}}</span>
        </div>
      </div>
    </div>
    <input type="text" v-model="submits" />
  </div>

</template>
<script>
  export default {
    name: 'app',
    data() {
      return {
        submits: 0,
        perLevel: [1, 2, 3, 5, 6, 7, 8],
        names: ['Player', 'Undergraduate', 'Graduate Student', 'Intern', 'Apprentice', 'Researcher', 'Manager', 'Lead Researcher'],
        colors: ['#3AE112','#34D430','#2FC84D','#29BB6B','#23AF88','#1DA2A6','#1896C3','#1289E1'],
      }
    },
     computed: {
      levelData() {
        var subs = this.sumbits > 4800 ? 4800 : this.submits;
        var i;
        for (i = 0; i < this.perLevel.length; i++) {
          subs -= this.perLevel[i] * 150;
          if (subs < 0) {
            return {
              left: -subs,
              done: this.perLevel[i] * 150 + subs, //sub before reducing
              level: i,
              levelName: this.names[i],
              color: this.colors[i]
            }
          }
        }
        return {
          left: 0,
          done: this.perLevel[this.perLevel.length - 1] * 150,
          level: this.perLevel.length,
          levelName: this.names[this.perLevel.length],
          color: this.colors[this.perLevel.length]
        }
      },
    }
  }
</script>
<style>
</style>