<template>
  <UApp>

    
    <UNavigationMenu :items="items">

    </UNavigationMenu>
    
 
  </UApp>
</template>

<script setup>
import { navigationMenu } from '#build/ui';

const items = [
    {
    label: 'Guide',
    icon: 'i-lucide-book-open',
    to: '/docs/getting-started',
    },
      {
        label: 'Introduction',
        description: 'Fully styled and customizable components for Nuxt.',
        icon: 'i-lucide-house'
      },
      {
        label: 'Installation',
        description: 'Learn how to install and configure Nuxt UI in your application.',
        icon: 'i-lucide-cloud-download'
      },
      {
        label: 'Icons',
        icon: 'i-lucide-smile',
        description: 'You have nothing to do, @nuxt/icon will handle it automatically.'
      },
      {
        label: 'GitHub',
        icon: 'i-simple-icons-github',
        badge: '6k',
        to: 'https://github.com/nuxt/ui',
        target: '_blank'
      },
      {
        label: 'TesteTiago',
        icon: 'i-lucide-circle-help'
        
      }
]
</script>