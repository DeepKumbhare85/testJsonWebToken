<template>
  <div>
    <button @click="createToken">Create Token</button>
    <button @click="verifyToken">Verify Token</button>
  </div>
</template>

<script setup>

import { sign, verify } from 'jsonwebtoken-esm';
let token;
const secret = 'my-secret'
const createToken = () => {
  console.log('hello')
  token = sign({ name: "deep" }, secret, { expiresIn: '10s' })
  console.log(token);
}

const verifyToken = () => {
  console.log('your token is : ', token)
  try {
    const decoded = verify(token, secret)
    console.log("Your decoded data: ", decoded);
  }
  catch {
    console.error('token expired try to create new token')
  }
}

</script>