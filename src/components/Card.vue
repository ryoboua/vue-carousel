<template>
  <div class="card">
    <img :src="data.image" />
    <div class="card-info">
      <h4>{{ data.name }}</h4>
      <p>{{ data.date }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    num: {
      type: [Number, String],
    },
    name: {
      type: String,
      default: "Britta Clay Art",
    },
    date: {
      type: String,
      default: "Sat, 24 October 2020",
    },
    image: {
      type: String,
      default:
        "https://s3-alpha-sig.figma.com/img/b477/81d0/3f9d385e829ff893089fb7ce89d9c81e?Expires=1589760000&Signature=JBMK6y8JMtelyffNpcG4oEPWNarvnMOEaKdzTiKSu1tSrOb0YMBkWVs1~zIkPISMZQ0JUxWN2-lRBlj1QI3QZt6Gt6QRA2JRrwUjbD55OyJFtSLNNLO-7wHqMaBEiEov2W3IV6fVzy0MEYyt9IYeiT83W0k1SCU1BrvNJINNpLoyuLCy5jW3HVvNtDTXt8GTW1b-VT~9QWBx3v70R-k0QrQam4mGKjhrizI6NGGV22AHRAO6rCT8bMmWr5CNYvVTZtmQDexRYwSMdsD8sSPds8yji-m6Fp4i9O24ZpUjKjRLU8u5-2~hzgpyUqpw1UENiLlxGPdHtJgYYqR75WmO7Q__&Key-Pair-Id=APKAINTVSUGEWH5XD5UA",
    },
    data: {
        type: Object
    },
  },
}
</script>

<style>
.card {
  width: 271px;
  height: 280px;
  background-color: #ffffff;
}

.card img {
  width: 271px;
  height: 170px;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  object-fit: cover;
  object-position: 0 68%;
}

.card-info {
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
  border-bottom: 1px solid #e5e5e5;
  border-left: 1px solid #e5e5e5;
  border-right: 1px solid #e5e5e5;
  text-align: center;
  margin-top: -6px;
  height: 110px;
}

.card-info h4 {
  padding-top: 30px;
  margin: 0;
}

.card-info p {
  margin: 0;
  color: #747069;
}
</style>
