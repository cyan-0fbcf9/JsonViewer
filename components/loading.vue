<template>
  <div class="loader p-3">
    <svg
      version="1.1"
      id="loader-1"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      x="0px"
      y="0px"
      width="40px"
      height="40px"
      viewBox="0 0 50 50"
      style="enable-background:new 0 0 50 50;"
      xml:space="preserve"
    >
      <path
        fill="#000"
        d="M43.935,25.145c0-10.318-8.364-18.683-18.683-18.683c-10.318,0-18.683,8.365-18.683,18.683h4.068c0-8.071,6.543-14.615,14.615-14.615c8.072,0,14.615,6.543,14.615,14.615H43.935z"
      >
        <animateTransform
          attributeType="xml"
          attributeName="transform"
          type="rotate"
          from="0 25 25"
          to="360 25 25"
          dur="0.8s"
          repeatCount="indefinite"
        />
      </path>
    </svg>
    <div class="loader-text my-2">
      <div class="lt-1">L</div>
      <div class="lt-2">O</div>
      <div class="lt-3">A</div>
      <div class="lt-4">D</div>
      <div class="lt-5">I</div>
      <div class="lt-6">N</div>
      <div class="lt-7">G</div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss">
$tab: 680px; // タブレット
$sp: 480px; // スマホ

@mixin tab {
  @media (max-width: ($tab)) {
    @content;
  }
}
@mixin sp {
  @media (max-width: ($sp)) {
    @content;
  }
}

.loader {
  height: auto;
  text-align: center;
  transform-origin: top center;
  transform: scale(150%);
  @include tab {
    transform: scale(100%);
  }
}

svg path,
svg rect {
  fill: var(--app-theme-purple);
}

.loader-text {
  color: var(--app-theme-purple);
  font-family: var(--app-font-rounded);
  user-select: none;

  div {
    padding: 0px 0.1rem;
    animation: lt_anim 1s ease-out 0s infinite forwards;
    -webkit-animation: lt_anim 1s ease-out 0s infinite forwards;
    display: inline-block;
  }

  .lt-1 {
    animation-delay: 0s;
  }
  .lt-2 {
    animation-delay: 0.1s;
  }
  .lt-3 {
    animation-delay: 0.2s;
  }
  .lt-4 {
    animation-delay: 0.3s;
  }
  .lt-5 {
    animation-delay: 0.4s;
  }
  .lt-6 {
    animation-delay: 0.5s;
  }
  .lt-7 {
    animation-delay: 0.6s;
  }

  @keyframes lt_anim {
    0% {
      transform: translateY(0%);
    }
    15% {
      transform: translateY(-30%);
    }
    30% {
      transform: translateY(0%);
    }
    100% {
      transform: translateY(0%);
    }
  }
}
</style>