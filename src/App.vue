

<script setup>

import ExpandableProfile from '@/components/ExpandableProfile.vue'

const profile1 = {
  firstName: 'MIHAIL',
  lastName: 'CALARAȘAN',
  textTop: 'Mihail Calarașan – documentary photographer, based in Chisinau, Moldova. Was born in Transnistria in 1993. Since the fall of 2017, he hasbeen working on a permanent basis with the Moldovan magazine “Oameni și Kilometri” as a photographer and journalist. Also, starting the same year, he has been working on long-term documentary projects about the Ukrainian Carpathians, Transnistria and Gagauzia.',
  images: [
    'scr/assets/images/misha/photo_1.jpg',
    'scr/assets/images/misha/photo_2.jpg',
    'scr/assets/images/misha/photo_3.jpg',
    'scr/assets/images/misha/photo_4.jpg',
    'scr/assets/images/misha/photo_5.jpg',
    'scr/assets/images/misha/photo_6.jpg',
    'scr/assets/images/misha/photo_7.jpg',
    'scr/assets/images/misha/photo_8.jpg',
    'scr/assets/images/misha/photo_9.jpg',
    'scr/assets/images/misha/photo_10.jpg',
    'scr/assets/images/misha/photo_11.jpg',
    'scr/assets/images/misha/photo_12.jpg',
  ],
  textMiddle: 'RADA\n' + 'This story began in 2017, when I first met Inna and her children in the Carpathian Mountains.\n' +
      'They had fled Luhansk because of the war and started a new life among the hills.\n' +
      'Since then, I kept returning — both as a photographer, and as someone who feels deeply connected to their story.\n' +
      'I grew up in Transnistria, where there was also a war. Maybe that’s why their journey became part of mine.\n' +
      '“Rada” is not about war. It’s about home. About quiet. About how children keep growing — no matter what.',
  linkText: 'Instagram:',
  linkAnchor: '@kalarashan',
  linkUrl: 'https://www.instagram.com/kalarashan?igsh=MXZwdDNzNDZoa3ZmMA==',
  siteText: 'Site:',
  siteAnchor: 'kalarashan.com',
  siteUrl: 'https://www.kalarashan.com/about',
}

const profile3 = {
  firstName: 'POLINA',
  lastName: 'SUROVOVA',
  textTop: 'In my art I explore how ancient culture is reflected in modern human. I work with ancient myths and fairy tales of the world, to find what connects of our time with our ancient natural beginnings. Part of my method is the use of digital technologies as a tool for interacting with the non-human space. I transform my ideas in painting in which I use methods of classical painting techniques, I seek in classical technology the expression of a new time.',
  images: [
    'scr/assets/images/polina/photo_1.jpg',
  ],
  textMiddle: 'This painting was painted during pregnancy. It was a time of rebirth from one state to another. The edges are blurred and the movement of the figure is duplicated, showing the movement into a new existence. The blanket of flowers is a metaphor for nature, through this experience I felt that a woman during pregnancy is as close and one with nature as never before.',
  linkText: 'Instagram:',
  linkAnchor: '@polinasurovova',
  linkUrl: 'https://www.instagram.com/polinasurovova?igsh=bjhxZnM4ZXh5NW1k',
  siteText: '',
  siteAnchor: '',
  siteUrl: '',
}

const profile4 = {
  firstName: 'OLGA (KISI)',
  lastName: 'FIRSOVA',
  textTop: 'KISI is a multimedia artist originally from Belarus, currently living and working in Amsterdam. She graduated with a degree in mathematics and worked as a programmer for over ten years before changing her professional path and completing her education at the School of Contemporary Art “Free Workshops” in Moscow.\nHer artistic practice explores themes of memory, interaction, and communication within contemporary society. In her work, she aims for a particular tone — a blend of irony and tenderness — which she believes allows for a more precise expression of complex emotions and states of being.',
  images: [
    'scr/assets/images/olga/photo_1.jpg',
  ],
  textMiddle: 'Lily Field\nThis picturesque work is part of the After Life series and is dedicated to the theme of memory. Its atmosphere is reminiscent of an old, faded photograph. Through images and color schemes, it explores the invisible but deeply felt connection with those who are no longer with us—a connection preserved in memories. The work reflects the fragility and strength of this inner connection, its ability to sustain, transform, and continue life even after loss.',
  linkText: 'Instagram:',
  linkAnchor: '@kisi.artist',
  linkUrl: 'https://www.instagram.com/kisi.artist?igsh=ZmJ1c2F0bmVyc2J6',
  siteText: '',
  siteAnchor: '',
  siteUrl: '',
}

const profile2 = {
  firstName: 'DASHA',
  lastName: 'GLUSHKOVA',
  textTop: 'Dasha Glukhova is a gallery photographer. She shoots stories in a documentary and poetic way. She works mostly on 35 mm film cameras, rarrelly on 120 mm film.\n\nGlukhova graduated from MSU university in art criticism department and advertising fild. She has defended a Phd about Creative technoly of PSA. For 5 years she investigated the difference between the creative process and the artist`s work in the context of the issues of the of the visual language based on different cultural codes.',
  images: [
    'scr/assets/images/dasha/photo_1.jpg',
    'scr/assets/images/dasha/photo_2.jpg',
    'scr/assets/images/dasha/photo_3.jpg',
    'scr/assets/images/dasha/photo_4.jpg',
    'scr/assets/images/dasha/photo_5.jpg',
    'scr/assets/images/dasha/photo_6.jpg',
    'scr/assets/images/dasha/photo_7.jpg',
    'scr/assets/images/dasha/photo_8.jpg',
    'scr/assets/images/dasha/photo_9.jpg',
    'scr/assets/images/dasha/photo_10.jpg',
  ],
  textMiddle: '',
  linkText: 'Instagram:',
  linkAnchor: '@glukhovadasha',
  linkUrl: 'https://www.instagram.com/glukhovadasha?igsh=MXJtbmJqeDNqdDV6MA==',
  siteText: 'Site:',
  siteAnchor: 'glukhova-dasha.com',
  siteUrl: 'https://glukhova-dasha.com/?fbclid=PAQ0xDSwLbaDxleHRuA2FlbQIxMQABpxeXYxM8JtBpUeUgZryI7eJGotlIFiKLg_zmRqNVpSjiTuevZYtVPNqA_3_N_aem_uv4hwWBAD3E7g8PZx5GDgQ',
}

const profile5 = {
  firstName: 'VALERIA',
  lastName: 'TITOVA',
  textTop: 'Valeria Titova is an art director specializing in neural network–based projects and the author of the Telegram channel ЭйАйЛера, dedicated to the intersection of art and artificial intelligence.\n' +
  'A graduate of the Faculty of Journalism at Moscow State University, she studied neurographics at BBE and works with 2D image and video generation using AI tools. Her artistic practice explores themes of socialization and nostalgia.\n' +
  'She has participated in exhibitions and festivals such as Zaryadye Park and NUR, and has been a multiple-time winner of the Prostor open call.',
  images: [
    'scr/assets/images/valeria/photo_1.PNG',
    'scr/assets/images/valeria/photo_2.PNG',
    'scr/assets/images/valeria/photo_3.PNG',
    'scr/assets/images/valeria/photo_4.PNG',
  ],
  textMiddle: 'Psyche 3.0: How High the Grass Grows is a piece of neurogenerative art that wanders through the fragile terrain of memory in the digital age.\nWhy do scandals vanish like smoke, memes flicker for a single day, and yet we whisper, "the internet remembers everything"?\nIs there a pixelated heaven where lost accounts rest?\nAnd what might we uncover if we step softly into the tall grass of forgotten data—among glimmers, ghosts, and digital echoes?',
  linkText: 'Instagram:',
  linkAnchor: '@lerarussia',
  linkUrl: 'https://www.instagram.com/lerarussia?igsh=MWprZHV2Z3E4a2JocQ==',
  siteText: '',
  siteAnchor: '',
  siteUrl: '',
}

</script>

<template>
  <div class="page">
    <div class="content">
      <div class="block image-block">
        <img src="/src/assetsscr/assets/images/header.png" alt="sonja" class="image-block_img" />
      </div>
      <div class="block text-block">
        <div class="text-block_text">
          WHILE THE GRASS IS IN BLOOM <br>
          -  an exhibition about unmeasurable bearings and rhythms that do not repeat, but return –
          <br><br>
          In the urban landscape, time becomes abstract. It dissolves into schedules, digital interfaces, movement algorithms, and what has been "done." In this context, the sense of presence is easily lost. You forget what your own rhythm sounds like. Nature is not an alternative, but an invitation to explore. Where the grass is in bloom, no one asks how long it will last. They simply know: it still is.
          <br><br>
          This exhibition emerged from a personal cycle: it opens on a birthday. A day when time doesn’t just pass, but seems to fold into itself. And you find yourself standing inside that loop, listening, looking around, trying to understand where you’ve returned from.
          <br><br>
          They say the meaning of life is to enjoy the passage of time. And it is essential to feel it. Because within that feeling lies a direction that requires no route. It cannot always be named, but it always invites you to stay. Grass here is not a theme, it is a way of being. This is about orientation through observation, where watching becomes movement. Through a gesture repeated not out of habit, but because something holds in it.
          <br><br>
          The exhibition becomes a space for such contact. Here, artists work with cycles, micro-movements, intimate rhythms, the body, memory, and what rings out in the pause. Sometimes they turn to nature directly: to blooming, vanishing, growth. And sometimes to other forms of orientation: found or invented.
          <br><br>
          While the grass is in bloom, you may simply be.
        </div>
      </div>
      <div class="block list-block">
        <div class="list-block_title">
          <div class="list-block_title_text">
            artists:
          </div>
        </div>
        <div class="list-block_list">
          <ExpandableProfile
              :data="profile1"
              name-position="left"
              arrow-position="right"
          />
          <ExpandableProfile
              :data="profile2"
              name-position="right"
              arrow-position="left"
          />
          <ExpandableProfile
              :data="profile3"
              name-position="left"
              arrow-position="right"
          />
          <ExpandableProfile
              :data="profile4"
              name-position="right"
              arrow-position="left"
          />
          <ExpandableProfile
              :data="profile5"
              name-position="left"
              arrow-position="right"
          />
          <div class="list-block_separator"></div>
        </div>
        <div class="block footer-block">
          <div class="footer-block_title">
            <div class="footer-block_title-1">
              SŒNYA
            </div>
            <div class="footer-block_title-2">
              GaIIary
            </div>
          </div>
          <div class="footer-block_text">
            <div class="footer-block_text-1">
              Web site by Filipp Gladisev
            </div>
            <div class="footer-block_text-2">
              Special thanks to Arsenii Bychkov for his help in organizing the exhibition.
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.page {
  background-color: var(--color-green-light);
  display: flex;
  justify-content: center;
  min-height: 100vh;
  padding: 0;
  margin: 0;
}

.content {
  width: 360px;
  display: flex;
  flex-direction: column;
}

.block {
  display: flex;
  align-items: center;
  justify-content: center;
}

.image-block {
  width: 100%;
}

.image-block_img {
 width: 100%;
}

.text-block {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-block: 2rem;
}

.text-block_text {
  width: 93%;
  font-size: 16px;
  color: var(--color-green-dark);
  font-family: "FirstNue", sans-serif;
}

.list-block {
  display: flex;
  flex-direction: column;
  background-color: var(--color-green-dark);
}

.list-block_title {
  margin-top: 1.5rem;
  margin-bottom: 4rem;
}

.list-block_title_text {
  font-size: 136px;
  color: var(--color-green-light);
  font-family: "PalaceScript", sans-serif;
}

.list-block_list{
  width: 100%;
}

.list-block_separator {
  height: 1px;
  width: 82%;
  background-color: var(--color-green-light);
  margin: 2rem auto 0 auto;
}

.footer-block {
  margin-top: 1rem;
  display: flex;
  flex-direction: column;
}

.footer-block_title {
  display: flex;
  align-items: center;
}

.footer-block_title-1{
  margin-right: 10px;
  color: var(--color-green-light);
  font-size: 16px;
  font-family: "FirstNue", sans-serif
}

.footer-block_title-2{
  color: var(--color-green-light);
  font-size: 12px;
  font-family: "FirstNue", sans-serif
}

.footer-block_text{
  margin-top: 1.5rem;
  margin-bottom: 1rem;
}

.footer-block_text-1{
  color: var(--color-green-light);
  font-size: 10px;
  font-family: "FirstNue", sans-serif;
  text-align: center;
}

.footer-block_text-2{
  color: var(--color-green-light);
  font-size: 10px;
  font-family: "FirstNue", sans-serif;
  text-align: center;
}
</style>
