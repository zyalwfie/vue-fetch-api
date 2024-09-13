<template>
  <div>
    loading <span></span>
  </div>
</template>

<style scoped>
div {
  font-size: 2rem;
  display: flex;
  justify-content: center;
  gap: 1rem;
  align-items: center;
  text-transform: capitalize;
}

div span {
  display: inline-block;
  width: 2rem;
  height: 2rem;
  border-radius: 9999rem;
  border-top: 5px solid blue;
  border-left: 5px solid blue;
  border-bottom: 5px solid blue;
  border-right: 5px solid transparent;
  animation: spin 1s linear infinite;
}


@keyframes spin {
	0% {
		transform: rotate(0deg);
	}
	100% {
		transform: rotate(360deg);
	}
}
</style>
