<template>
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
</template>

<script>
export default {
  name: 'footerBottom',
};
</script>
