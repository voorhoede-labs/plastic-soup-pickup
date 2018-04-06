<template>
  <footer>
    <img class="image" src="http://plasticsoupsurfer.org/assets/icons/footer-wave.svg" alt="">
    <div class="footer-content">
      <share-on-facebook/>
      <share-on-twitter/>
      <h3>Press & Interviews</h3>
      <ul>
        <li>Martine Eyzenga</li>
        <li><a href="mailto:martine@diezijnvaardig.nl">martine@diezijnvaardig.nl</a></li>
        <li>06 54 28 54 92</li>
      </ul>

      <h3>Campaign & Programming</h3>
      <ul>
        <li>Kim van den Anker</li>
        <li><a href="mailto:kimvdanker@gmail.com">kimvdanker@gmail.com</a></li>
        <li>06 31 91 77 34</li>
      </ul>
      <a href="http://plasticsoupsurfer.us9.list-manage1.com/subscribe?u=913b66d5123f4d287fe729350&amp;id=956e13cc1f" class="button button-donate">Newsletter</a>
    </div>
  </footer>
</template>
<script>
import ShareOnFacebook from 'components/ShareOnFacebook.vue'
import ShareOnTwitter from 'components/ShareOnTwitter.vue'

export default {
  components: {
    ShareOnFacebook,
    ShareOnTwitter
  }
}

</script>
<style>
  footer {
    width: 100%;
  }

  .image {
    width: 200%;
    margin-left: -200px;
    position: relative;
    bottom: -10px;
  }

  .footer-content {
    color: #fff;
    width: 100%;
    padding: 1em 0;
    margin: 0 auto;
    background: #2b2f47;
    padding: 2em;
  }

  .footer-content > h3 {
    text-transform: uppercase;
    margin-top: 1em;
  }

  .button-donate {
    padding: .8em 3em;
    border-radius: 0;
    margin-top: 2em;
    font-size: 1em;
    font-weight: 400;
  }

  a {
    color: #fff;
  }
</style>

<script>

</script>

