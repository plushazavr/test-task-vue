<template>
  <div class="app">
    <div class="inventory">
      <div class="preview">
        <img src="./img/Img.jpg" class="preview__img" alt="preview"/>
        <div class="preview__text">
          <hr class="line-one"/>
          <hr class="line-two"/>
          <hr class="line-three"/>
          <hr class="line-four"/>
          <hr class="line-five"/>
          <hr class="line-six"/>
          <hr class="line-seven"/>
        </div>
      </div>
      <div class="inventory__grid">
          <div class="cell cell" v-for="ivent in ivents" :key="ivent" @click="modalVisible = true">
            <img :src="`${ivent.src}`" class="cell__img"/>
            <div class="cell__counter">
              <p class="cell__count">{{ ivent.counter }}</p>
            </div>
          </div>

          <div v-if="modalVisible">
            <div class="inventory__modal" v-for="ivent in ivents" :key="ivent">
              <button @click="modalVisible = false" class="button__close"></button>
              <img :src="`${ivent.src}`" class="modal__img" alt="" />
              <hr class="line-zero" />
              <hr class="line-one" />
              <hr class="line-two" />
              <hr class="line-three" />
              <hr class="line-four" />
              <hr class="line-seven" />
              <hr class="line-zero" />
              <button class="button__delete">Удалить предмет</button>
            </div>
          </div>
          

      
      </div>
    </div>
    <div class="hint">
      <div class="hint__skeleton"></div>
      <button class="button__close"></button>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      ivents: [
        {id: 1, counter: 4, src: require('./img/img-1.png')}, // преобразование пути к картинке в запрос модуля через require
        {id: 2, counter: 2, src: require('./img/img-2.png')},
        {id: 3, counter: 5, src: require('./img/img-3.png')}
      ],
      modalVisible: false,
      
    }
  }, 

  methods: {
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  }

.app {
  background-color: #1D1D1D;
  max-width: 849px;
  height: 660px;
  padding: 32px;
}

.inventory {
  margin: 0;
  width: 785px;
  height: 500px;
  margin-bottom: 24px;
  display: flex;
  justify-content: space-between;
}

.preview__img {
  width: 208px;
  border-radius: 12px;
  margin-bottom: 20px;
}

.preview__text {  
  width: 208px;
  height: 198px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}

.line-zero {
  width: 220px;
  height: 1px;
  background: #4D4D4D;
}
.line-one {
  width: 190px;
  height: 26px;
  background: linear-gradient(90deg, #3C3C3C 0%, #444444 51.04%, #333333 100%);
  border-radius: 8px;
  border: none;
}

.line-two {
  width: 155px;
  height: 10px;
  background: linear-gradient(90deg, #3C3C3C 0%, #444444 51.04%, #333333 100%);
  border-radius: 4px;
  border: none;
}

.line-three {
  width: 190px;
  height: 10px;
  background: linear-gradient(90deg, #3C3C3C 0%, #444444 51.04%, #333333 100%);
  border-radius: 4px;
  border: none;
}

.line-four {
  width: 170px;
  height: 10px;
  background: linear-gradient(90deg, #3C3C3C 0%, #444444 51.04%, #333333 100%);
  border-radius: 4px;
  border: none;
}

.line-five {
  width: 160px;
  height: 10px;
  background: linear-gradient(90deg, #3C3C3C 0%, #444444 51.04%, #333333 100%);
  border-radius: 4px;
  border: none;
}

.line-six {
  width: 140px;
  height: 10px;
  background: linear-gradient(90deg, #3C3C3C 0%, #444444 51.04%, #333333 100%);
  border-radius: 4px;
  border: none;
}

.line-seven {
  width: 80px;
  height: 10px;
  background: linear-gradient(90deg, #3C3C3C 0%, #444444 51.04%, #333333 100%);
  border-radius: 4px;
  border: none;
}

.preview {
  padding: 18px 14px 24px 14px;
  width: 236px;
  height: 500px;
  background: #262626;
  border: 1px solid #4D4D4D;
  border-radius: 12px;
}

.inventory__grid{
  position: relative;
  /* width: 525px; */
  /* background: #4D4D4D; */
  background: #262626;
  /* border-radius: 12px; */

  display: grid; 
  grid-template-columns: repeat(5, 105px);
  grid-template-rows: repeat(5, 100px); 
  gap: 1px 1px;
}

.line2 {
  border-radius: 12px 0px 0px 0px; 
}

.cell {
  cursor: pointer;
  
  background: #262626;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0px 0px 0px 1px #4D4D4D;
}

.cell__img {
  width: 54px;
  height: 54px;
  /* background-image: url(./img/img-1.png); */
  background-position: center;
  background-repeat: no-repeat;
  background-size: 54px 54px;
}
.cell__counter {
  position: absolute;
  bottom: 0px;
  right: 0px;
  width: 16px;
  height: 16px;
  background: #262626;
  border: 1px solid #4D4D4D;
  border-radius: 6px 0px 0px 0px;
}

.cell__count {
  margin: 0;
  padding: 0;
  font-family: 'Inter';
  font-style: normal;
  font-weight: 500;
  font-size: 10px;
  line-height: 12px;
  text-align: center;
  color: #FFFFFF;
  opacity: 0.4;
}

.inventory__modal {
  width: 250px;
  height: 500px;
  padding: 55px 20px 18px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  position: absolute;
  top: 0;
  right: 0;
  background: rgba(38, 38, 38, 0.5);
  border-left: 1px solid #4D4D4D;
  backdrop-filter: blur(8px);
}

.modal__img {
  width: 130px;
  height: 130px;
  margin-bottom: 30px;
}

.hint {
  position: relative;
  width: 785px;
  height: 72px;
  background: #262626;
  border: 1px solid #4D4D4D;
  border-radius: 12px;
  padding: 18px;
}

.hint__skeleton {
  width: 699px;
  height: 36px;
  background: linear-gradient(90deg, #3C3C3C 0%, #444444 51.04%, #333333 100%);
  border-radius: 12px;
}

.button__close {
  cursor: pointer;
  position: absolute;
  top: 8px;
  right: 8px;
  width: 24px;
  height: 24px;
  background-image: url(./img/btn-close.png);
  background-repeat: no-repeat;
  background-position: center;
  border: none;
  background-color: transparent;
}

.button__delete {
  width: 220px;
  height: 39px;
  background: #FA7272;
  border-radius: 8px;
  border: none;
  cursor: pointer;

  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 17px;
  text-align: center;
  color: #FFFFFF;
}
</style>