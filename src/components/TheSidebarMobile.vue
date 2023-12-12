<template>
  <TheSidebarMobileOverlay>
    <aside class="w-64 max-h-screen overflow-auto bg-white">
            <section class="flex items-center p-4 border-b sticky top-0 bg-white">
                <button class="ml-2 mr-6 focus:outline-none">
                    <BaseIcon name="menu"></BaseIcon>
                </button>
                <LogoMain></LogoMain>
            </section>
            <SidebarContent></SidebarContent>
        </aside>
  </TheSidebarMobileOverlay>
</template>

<script>
import TheSidebarMobileOverlay from './TheSidebarMobileOverlay.vue'
import SidebarContent from './SidebarContent.vue'
import LogoMain from './LogoMain.vue'
import BaseIcon from './BaseIcon.vue'

export default {
  components: { TheSidebarMobileOverlay, SidebarContent, LogoMain, BaseIcon }
}
</script>