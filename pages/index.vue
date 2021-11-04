<script src="https://identity.netlify.com/v1/netlify-identity-widget.js"></script>
<template>
  <div>Hi</div>
</template>

<script>
  if (window.netlifyIdentity) {
    window.netlifyIdentity.on("init", user => {
      if (!user) {
        window.netlifyIdentity.on("login", () => {
          document.location.href = "/admin/";
        });
      }
    });
  }
</script>