<template>
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
</template>

<script>
export default {
  name: 'mainContentHeader',
};
</script>
