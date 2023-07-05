<template>
    <div class="splashscreen">
        <img 
            src="@/assets/dinerodinero-icon.svg" 
            alt="Logo" 
        />
        <h1><span>dinero</span>dinero</h1>
    </div>
</template>

<style scoped>
.splashscreen {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100vh;
}
h1 {
  color: var(--brand-blue);
}
h1 span {
  color: var(--brand-green);
}
</style>