<template>
  <div class="modal" v-if="isOpen">
    <div class="modal__body">
      <div class="modal__images">
        <img
          :src="getImgUrl(data.img)"
          :alt="data.alt"
        />
        <div class="modal__preview">
          <img
            src="@/assets/IMG/preview-1.jpg"
            alt="Классная футболка! Эволюционируй или сдохни"
            width="50"
            height="50"
          />
          <img
            class="active"
            src="@/assets/IMG/preview-2.jpg"
            alt="Классная футболка! Эволюционируй или сдохни"
            width="50"
            height="50"
          />
          <img
            src="@/assets/IMG/preview-3.jpg"
            alt="Классная футболка! Эволюционируй или сдохни"
            width="50"
            height="50"
          />
        </div>
      </div>
      <div class="modal__description">
        <h1 class="modal__title"> {{ data.name }}</h1>
        <form class="modal__form" action="#" method="GET">
          <div class="modal__sell">
            <div class="modal__scores">
              <h6 class="modal__score"> {{ data.price }} баллов</h6>
              <button class="btn-primary" type="submit">Заказать</button>
            </div>
            <div class="modal__yourbalance">
              <p class="modal__yourbalance--balance">Твой баланс:</p>
              <p class="modal__yourbalance--score">3 945 баллов</p>
              <img
                class="modal__yourbalance--basket"
                src="@/assets/IMG/basket.png"
                alt="Корзина"
              />
            </div>
          </div>
          <div class="modal__radio--colors">
            <h6 class="modal__radio--title">Цвета:</h6>
            <div class="modal__radio--btns">
              <input
                class="modal__radio"
                type="radio"
                name="modal__color"
                id="modal__color--blue"
                value="#00458A"
              />
              <label class="modal__color--label" for="modal__color--blue">
                <div
                  class="modal__color--container"
                  style="background-color: #00458a"
                ></div>
                <span>Синий</span>
              </label>
              <input
                class="modal__radio"
                type="radio"
                name="modal__color"
                id="modal__color--beige"
                value="#EFE8D8"
              />
              <label class="modal__color--label" for="modal__color--beige">
                <div
                  class="modal__color--container"
                  style="background-color: #efe8d8"
                ></div>
                <span>Бежевый</span>
              </label>
              <input
                class="modal__radio"
                type="radio"
                name="modal__color"
                id="modal__color--gray"
                value="#D4D4DA"
              />
              <label class="modal__color--label" for="modal__color--gray">
                <div
                  class="modal__color--container"
                  style="background-color: #d4d4da"
                ></div>
                <span>Серый</span>
              </label>
            </div>
          </div>
          <div class="modal__radio--size">
            <h6 class="modal__radio--title">Размер:</h6>
            <div class="modal__radio--btns">
              <input
                class="modal__radio"
                type="radio"
                name="modal__size"
                id="modal__size--s"
                value="s"
              />
              <label class="modal__size--label" for="modal__size--s">
                <span>S</span>
              </label>
              <input
                class="modal__radio"
                type="radio"
                name="modal__size"
                id="modal__size--m"
                value="m"
              />
              <label class="modal__size--label" for="modal__size--m">
                <span>M</span>
              </label>
              <input
                class="modal__radio"
                type="radio"
                name="modal__size"
                id="modal__size--l"
                value="l"
              />
              <label class="modal__size--label" for="modal__size--l">
                <span>L</span>
              </label>
            </div>
          </div>
          <div class="modal__info">
            <h6 class="modal__info--title">Детали:</h6>
            <p class="modal__info--text">
              {{ data.details }}
            </p>
            <h6 class="modal__info--title">Как выбрать размер:</h6>
            <p class="modal__info--text">Написать дяде Рику для уточнения.</p>
          </div>
          <button class="modal__close" type="button" @click="closeModal">
            <img src="@/assets/IMG/close.svg" alt="Знак икс" />
          </button>
        </form>
      </div>
    </div>
    <div class="overlay" @click="closeModal"></div>
  </div>

</template>

<script>
export default {
  name: 'modal',
  props: {
    isOpen: Boolean,
    data: Object,
  },
  data() {
    return {
      isShowModal: false,
    };
  },
  methods: {
    closeModal() {
      this.$emit('close');
    },
    getImgUrl(data) {
      // eslint-disable-next-line global-require,import/no-dynamic-require,import/extensions
      return require(`@/assets/IMG/${data}`);
    },
  },
};
</script>
