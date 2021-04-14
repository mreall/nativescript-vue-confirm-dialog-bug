<template>
  <Page>
    <ActionBar>
      <Label text="Home" />
    </ActionBar>

    <GridLayout>
      <Label class="info">
        <FormattedString>
          <Span class="fas" text.decode="&#xf135; " />
          <Span :text="message" />
        </FormattedString>
      </Label>
      <Button text="Open confirm dialog" @tap="onTap" />
    </GridLayout>
  </Page>
</template>

<script>
export default {
  computed: {
    message() {
      return "Blank {N}-Vue app";
    },
  },

  methods: {
    onTap() {
      console.log(`Confirm dialog should open now.`);
      confirm({
        title: "Confirm",
        message: "Does the dialog appear?",
        okButtonText: "Yes",
        cancelButtonText: "No",
        cancelable: true,
      }).then((res) => {
        console.log(`Confirm dialog closed.`);
      });
    },
  },
};
</script>

<style scoped lang="scss">
@import "@nativescript/theme/scss/variables/blue";

// Custom styles
.fas {
  @include colorize($color: accent);
}

.info {
  font-size: 20;
  horizontal-align: center;
  vertical-align: center;
}
</style>
