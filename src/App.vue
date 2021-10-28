<template>
  <div class="wrapper">
    <div class="container container__inner">
      <asideLeft></asideLeft>
      <section class="main-content main-content__left">
        <mainContentHeader></mainContentHeader>
        <a class="banner" href="#">
          <img src="@/assets/IMG/Баннер.jpg" alt="баннер" />
        </a>
        <div class="point-btns">
          <a class="point-btns__item" style="background-color: #eff8eb">
            <img
              class="point-btns__img"
              src="@/assets/IMG/plus.png"
              alt="Знак плюс"
            />
            <span class="point-btns__text">Получить баллы</span>
          </a>
          <a class="point-btns__item" style="background-color: #e9f2fb">
            <img
              class="point-btns__img"
              src="@/assets/IMG/question.png"
              alt="Вопросительный знак"
            />
            <span class="point-btns__text">Как получить баллы</span>
          </a>
          <a class="point-btns__item" style="background-color: #fffae7">
            <img
              class="point-btns__img"
              src="@/assets/IMG/sbox.png"
              alt=" Знак подарка"
            />
            <span class="point-btns__text">Подарить баллы</span>
          </a>
        </div>
        <div class="tabs-btns">
          <button
            v-for="tab in tabs"
            :key="tab.key"
            class="main__tab"
            :class="
              {active: tab.key === activeTabKey }
            "
            @click="myFilter(tab)"
            type="button"
          >
            {{ tab.name }}
          </button>
        </div>
        <div class="main-cards js-cards">
          <div class="main-cards__item" v-for="item in filterItems" :key="item.id">
            <img
              class="main-cards__img"
              :src="getImgUrl(item.img)"
              :alt="item.alt"
            />
            <span v-if="item.span" class="badge">NEW</span>
            <div class="main-cards-info">
              <h6 class="main-cards__points">{{item.price}} баллов</h6>
              <p class="main-cards__title">
                {{ item.name }}
              </p>
              <p class="main-cards__size">{{ item.size }}</p>
              <button class="main-cards-btn" type="button" @click="openCard(item)">
                Заказать
              </button>
            </div>
          </div>
        </div>
      </section>
    </div>
    <footerBottom></footerBottom>
    <modal :data="modalData" :is-open="isShowModal" @close="closeModal"></modal>
  </div>
</template>

<script>
import modal from '@/components/modal.vue';
import footerBottom from '@/components/footer.vue';
import mainContentHeader from '@/components/mainContentHeader.vue';
import asideLeft from '@/components/aside.vue';

export default {
  name: 'app',
  components: {
    modal,
    footerBottom,
    mainContentHeader,
    asideLeft,
  },
  data() {
    return {
      isShowModal: false,
      modalData: {},
      isActive: false,
      activeTabKey: 'all',
      clothes: [
        {
          id: 0,
          img: '2.jpg',
          span: true,
          price: 120,
          size: 'Размеры S/M/L',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Футболка "Синий"',
          alt: 'Футболка',
        },

        {
          id: 1,
          img: '3.jpg',
          span: true,
          price: 220,
          size: 'Размеры S/M/L',
          details:
            'Хлопок 80%',
          name: 'Футболка Эволюция',
          alt: 'Футболка',
        },

        {
          id: 2,
          img: '1.jpg',
          span: true,
          price: 320,
          size: 'Размеры S/M/L',
          details:
            'Вискоза 20%',
          name: 'Футболка "Салатовый"',
          alt: 'Футболка',
        },
        {
          id: 3,
          img: '4.jpg',
          span: false,
          price: 420,
          size: 'Размеры S/M/L',
          details:
            'Материал: Хлопок 0%, Вискоза 20%',
          name: 'Футболка "Серый"',
          alt: 'Футболка',
        },
        {
          id: 4,
          img: '5.jpg',
          span: false,
          price: 520,
          size: 'Размеры S/M/L',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Футболка "Черный"',
          alt: 'Футболка',
        },
        {
          id: 5,
          img: 't-shirt.jpg',
          span: false,
          price: 620,
          size: 'Размеры S/M/L',
          details:
            'Материал: Хлопок 80%, Вискоза 20%',
          name: 'Футболка "Эволюционируй или сдохни"',
          alt: 'Футболка',
        },
      ],
      accesories: [
        {
          id: 6,
          img: '6.jpg',
          span: true,
          price: 20,
          size: '',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Носки',
          alt: 'Футболка',
        },

        {
          id: 7,
          img: '7.jpg',
          span: true,
          price: 30,
          size: '',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Носки',
          alt: 'Футболка',
        },

        {
          id: 8,
          img: '8.jpg',
          span: true,
          price: 40,
          size: '',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Носки',
          alt: 'Футболка',
        },
        {
          id: 9,
          img: '9.jpg',
          span: false,
          price: 50,
          size: '',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Носки',
          alt: 'Футболка',
        },
        {
          id: 10,
          img: '10.jpg',
          span: false,
          price: 60,
          size: '',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Носки',
          alt: 'Футболка',
        },
        {
          id: 11,
          img: '11.jpg',
          span: false,
          price: 70,
          size: '',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Носки',
          alt: 'Футболка',
        },
      ],
      tabs: [
        {
          key: 'all',
          name: 'Все товары',
        },
        {
          key: 'clothes',
          name: 'Одежда',
        },
        {
          key: 'accesories',
          name: 'Аксессуары',
        },
      ],
    };
  },
  computed: {
    filterItems() {
      if (this.activeTabKey === 'clothes') {
        return [...this.clothes];
      } if (this.activeTabKey === 'accesories') {
        return [...this.accesories];
      }
      return [...this.clothes, ...this.accesories].sort((a, b) => Number(b.span) - Number(a.span));
    },
  },
  methods: {
    openCard(data) {
      this.openModal();
      this.modalData = data;
    },
    openModal() {
      this.isShowModal = true;
    },
    closeModal() {
      this.isShowModal = false;
    },
    getImgUrl(item) {
      // eslint-disable-next-line global-require,import/no-dynamic-require,import/extensions
      return require(`./assets/IMG/${item}`);
    },
    myFilter(tab) {
      this.activeTabKey = tab.key;
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/SCSS/main.scss";
</style>
