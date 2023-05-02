<template>
  <div>
    Hello World!

    <form id="card-form" class="payment-form" onsubmit="alert('hello!')">
      <div id="card-container"></div>
      <button type="submit">Pay</button>
    </form>
  </div>
</template>

<script setup>
useHead({
  link: [{
    rel: 'manifest',
    href: 'manifest.json'
  }],
  script: [{
    hid: 'square-sdk',
    src: 'https://sandbox.web.squarecdn.com/v1/square.js',
  }]
})

onMounted(async () => {
  const SQUARE_APPLICATION_ID = "sandbox-sq0idb-gQCtis_1gvFl5rguGUXNRQ";
  const SQUARE_ECOMM_LOCATION_ID = "L5R1RKYHWDVV0";

  const payments = Square.payments(
    SQUARE_APPLICATION_ID,
    SQUARE_ECOMM_LOCATION_ID
  )

  const card = await payments.card()
  await card.attach('#card-container')
})


</script>
