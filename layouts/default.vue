<template>
  <div>
    <nuxt />
  </div>
</template>

<style lang="scss">
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.btn-ghost {
  padding: 12px 32px;
  color: white;
  text-decoration: none;
  border: 1px solid white;
  display: inline-block;
  text-transform: uppercase;
  margin: 15px 0;
  font-weight: 600;
  transition: ease-out 0.3s;

  &:hover {
    background: white;
    color: #2e3442;
  }

}
</style>
