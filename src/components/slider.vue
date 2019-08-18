<template>
 <div class="slwrap" id='slider'>
   <div class="slider__btn" v-on:click='prevSlide'><img class="slider__btn-icon" src="../assets/prev.svg" alt="prev"></div>
	 <div class="slider__btn slider__btn_next" v-on:click='nextSlide'><img class="slider__btn-icon" src="../assets/next.svg" alt="next"></div>

	<div class='slider js-slider'>
		<div class="slider__body" v-bind:style='{left: sliderOffsetLeft + "px"}'>
			<ul class="slider__slide" >
        <li class="slider__slide js-slide">
            <div class="slider__slide-video">
              <video width="549px"  height="327px" controls="controls" poster="../assets/video_poster.png">
                 <source src="" >
              </video>
            </div>
            <div class="slider__slide-text">
              <span class="slider__slide-text_gold">the cool</span>
              <span class="slider__slide-text_white">the minimal</span>
            </div>
        </li>
        <li class="slider__slide js-slide">
            <div class="slider__slide-text">
              <span class="slider__slide-text_gold">the cool</span>
              <span class="slider__slide-text_white">the minimal</span>
            </div>
        </li>
      </ul>
		</div>
	</div>
 </div>
</template>

<script>

export default {
 el: '#app',

	data () {
		return {
			// Всего слайдов
      sliderAllCount: 0,
      // Номер активного слайда
      sliderActive: 1,
      // Отступ тела со слайдами в контейнере
      sliderOffsetLeft: 0,
      // Шаг одного слайда = его длина
      sliderOffsetStep: 0,
		}
	},

	methods: {
    // Иницилизация слайдера
    initSlider: function () {
			// Получаем элементы сладера и его слайдов
      let sliderBody = this.$el.querySelector('.js-slider')
      let sliderSlidies = sliderBody.querySelectorAll('.js-slide')
			// Записываем длину одного слайда для перелистывания
      this.sliderOffsetStep = sliderBody.clientWidth
			// Общее количество слайдов для стопов
      this.sliderAllCount = sliderSlidies.length
    },

		// Открыть слайд по номеру
    openSlide: function (id) {
      if (id > 0 && id <= this.sliderAllCount) {
        this.sliderActive = id
				// Сдвигаем элемент со слайдами
        this.sliderOffsetLeft = -(this.sliderActive * this.sliderOffsetStep - this.sliderOffsetStep)
      }
    },

    // Следующий слайд
    nextSlide: function () {
      if (this.sliderActive < this.sliderAllCount) {
        this.sliderActive += 1
				this.openSlide(this.sliderActive)
      }
    },

    // Предыдущий слайд
    prevSlide: function () {
      if (this.sliderActive > 1) {
        this.sliderActive -= 1
				this.openSlide(this.sliderActive)
      }
    }
  },

  mounted () {
    this.initSlider()

    // Перенастройка слайдера при ресайзе окна
    window.addEventListener('resize', () => {
      this.initSlider()
      this.openSlide(this.sliderActive)
    })
  }
}
</script>
