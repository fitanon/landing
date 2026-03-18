<script setup lang="ts">
const columns = [{
  label: 'Product',
  children: [{
    label: 'Features',
    to: '#features'
  }, {
    label: 'Pricing',
    to: '#pricing'
  }, {
    label: 'Changelog'
  }, {
    label: 'Roadmap'
  }]
}, {
  label: 'Privacy',
  children: [{
    label: 'Privacy Policy'
  }, {
    label: 'Terms of Service'
  }, {
    label: 'Data Handling'
  }, {
    label: 'Security'
  }]
}, {
  label: 'Company',
  children: [{
    label: 'About'
  }, {
    label: 'Blog'
  }, {
    label: 'Careers'
  }, {
    label: 'Contact'
  }]
}]

const toast = useToast()

const email = ref('')

function onSubmit() {
  toast.add({
    title: 'Subscribed!',
    description: 'You\'ve been subscribed to our newsletter.'
  })
  email.value = ''
}
</script>

<template>
  <USeparator
    icon="i-lucide-dumbbell"
    class="h-px"
  />

  <UFooter :ui="{ top: 'border-b border-default' }">
    <template #top>
      <UContainer>
        <UFooterColumns :columns="columns">
          <template #right>
            <form @submit.prevent="onSubmit">
              <UFormField
                name="email"
                label="Stay in the loop"
                size="lg"
              >
                <UInput
                  v-model="email"
                  type="email"
                  class="w-full"
                  placeholder="Enter your email"
                >
                  <template #trailing>
                    <UButton
                      type="submit"
                      size="xs"
                      label="Subscribe"
                    />
                  </template>
                </UInput>
              </UFormField>
            </form>
          </template>
        </UFooterColumns>
      </UContainer>
    </template>

    <template #left>
      <p class="text-sm text-muted">
        Fitanon — Train hard. Stay private. © {{ new Date().getFullYear() }}
      </p>
    </template>

    <template #right>
      <UButton
        to="https://instagram.com/fitanon"
        target="_blank"
        icon="i-simple-icons-instagram"
        aria-label="Fitanon on Instagram"
        color="neutral"
        variant="ghost"
      />
      <UButton
        to="https://x.com/fitanon"
        target="_blank"
        icon="i-simple-icons-x"
        aria-label="Fitanon on X"
        color="neutral"
        variant="ghost"
      />
      <UButton
        to="https://github.com/fitanon"
        target="_blank"
        icon="i-simple-icons-github"
        aria-label="Fitanon on GitHub"
        color="neutral"
        variant="ghost"
      />
    </template>
  </UFooter>
</template>
