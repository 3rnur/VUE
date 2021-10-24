<template>
  <div class="wrapper">
    <div class="container container__inner">
      <aside class="aside">
        <nav class="nav">
          <a href="#">
            <img
              class="logo"
              src="@/assets/IMG/Kolesagroup.svg"
              alt="логотип"
            />
          </a>
          <ul class="nav__menu">
            <li class="nav__list">
              <a class="nav__link" href="#"> Оргсхема </a>
            </li>
            <li class="nav__list">
              <a class="nav__link" href="#"> Kolesa Team </a>
            </li>
            <li class="nav__list">
              <a class="nav__link active" href="#"> Kolesa Shop </a>
            </li>
            <li class="nav__list">
              <a class="nav__link" href="#"> Новости </a>
            </li>
            <li class="nav__list">
              <a class="nav__link" href="#"> Education </a>
            </li>
            <li class="nav__list">
              <a class="nav__link" href="#"> Guidelines </a>
            </li>
            <li class="nav__list">
              <a class="nav__link" href="#"> Библиотека </a>
            </li>
            <li class="nav__list">
              <a class="nav__link" href="#"> FAQ </a>
            </li>
          </ul>
        </nav>
      </aside>
      <section class="main-content main-content__left">
        <div class="main-content__header">
          <div class="search">
            <button class="search__button" type="button">
              <img src="@/assets/IMG/search-big.svg" alt="" />
            </button>
            <input class="search__input" type="text" placeholder="Поиск" />
          </div>
          <a class="user">
            <div class="user__avatar">
              <img
                src="@/assets/IMG/avatar.jpg"
                alt="Аватар ползовательля"
                width="44"
                height="44"
              />
            </div>
            <div class="user__info">
              <span class="user__name">Мортиджан</span>
              <span class="user__point">300 баллов</span>
            </div>
          </a>
        </div>
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
              <button class="main-cards-btn" type="button" @click="openModal">
                Заказать
              </button>
            </div>
          </div>
        </div>
      </section>
    </div>
    <footer class="footer">
      <div class="container">
        <div class="footer__inner">
          <div class="footer__left">
            <p class="copyright">© Kolesa Group</p>
            <ul class="socety">
              <li class="socety__item">
                <a href="#">
                  <img src="@/assets/IMG/Instagram.svg" alt="инстагарм" />
                </a>
              </li>
              <li class="socety__item">
                <a href="#">
                  <img src="@/assets/IMG/YouTube.svg" alt="ютуб" />
                </a>
              </li>
              <li class="socety__item">
                <a href="#">
                  <img src="@/assets/IMG/VK.svg" alt="вконтакте" />
                </a>
              </li>
            </ul>
          </div>
          <div class="footer__right">
            <p class="footer__text">
              Есть идеи что улучшить? <br />
              Не знаешь, с кем решить проблему?
            </p>
            <button class="footer__btn" type="button">Написать</button>
          </div>
        </div>
      </div>
    </footer>
    <div class="modal" v-if="isShowModal">
      <div class="modal__body">
        <div class="modal__images">
          <img
            src="@/assets/IMG/t-shirt.jpg"
            alt="Классная футболка! Эволюционируй или сдохни"
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
          <h1 class="modal__title">Футболка "Эволюционируй или сдохни"</h1>
          <form class="modal__form" action="#" method="GET">
            <div class="modal__sell">
              <div class="modal__scores">
                <h6 class="modal__score">100 баллов</h6>
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
                Брендированная толстовка от Qazaq Republic. Материал: Хлопок
                80%, Вискоза 20%
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
    </div>
    <div class="overlay" v-if="isShowModal" @click="closeModal"></div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      isShowModal: false,
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
          name: 'Футболка "Эволюционируй или сдохни"',
          alt: 'Футболка',
        },

        {
          id: 1,
          img: '3.jpg',
          span: true,
          price: 220,
          size: 'Размеры S/M/L',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Футболка "Эволюционируй или сдохни"',
          alt: 'Футболка',
        },

        {
          id: 2,
          img: '1.jpg',
          span: true,
          price: 320,
          size: 'Размеры S/M/L',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Футболка "Эволюционируй или сдохни"',
          alt: 'Футболка',
        },
        {
          id: 3,
          img: '4.jpg',
          span: false,
          price: 420,
          size: 'Размеры S/M/L',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
          name: 'Футболка "Эволюционируй или сдохни"',
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
          name: 'Футболка "Эволюционируй или сдохни"',
          alt: 'Футболка',
        },
        {
          id: 5,
          img: 't-shirt.jpg',
          span: false,
          price: 620,
          size: 'Размеры S/M/L',
          details:
            'Брендированная футболка от Qazaq Republic. Материал: Хлопок 80%, Вискоза 20%',
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
