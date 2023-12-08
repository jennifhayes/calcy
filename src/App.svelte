<script>
  import Calculator from "./components/Calculator.svelte";
</script>

<main>
  <Calculator />
</main>

<style>
  main {
    display: grid;
    place-items: center;
    height: 100dvh;
    background-color: #c9c9c9;
    position: relative;
    overflow: hidden;
    isolation: isolate;
  }

  main::before {
    content: "";
    position: absolute;
    left: 36%;
    top: 50%;
    width: 200px;
    height: 200px;
    background-image: linear-gradient(rgb(78, 122, 219), rgb(40, 50, 139));
    animation: up-down 10s linear infinite;
    border-radius: 50%;
  }

  main::after {
    content: "";
    position: absolute;
    left: 50%;
    top: 25%;
    width: 200px;
    height: 200px;
    background-image: linear-gradient(rgb(211, 72, 148), rgb(196, 118, 17));
    animation: down-up 10s linear infinite;
    z-index: -1;
    border-radius: 50%;
  }

  @keyframes down-up {
    50% {
      transform: translateY(-150px);
    }

    to {
      transform: translateY(0);
    }
  }

  @keyframes up-down {
    50% {
      transform: translateY(150px);
    }

    to {
      transform: translateY(0);
    }
  }
</style>
