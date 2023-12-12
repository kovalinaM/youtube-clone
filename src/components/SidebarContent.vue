<template>
    <SidebarSection>
        <ul>
            <SidebarNavItem label="Home" icon="home" is-active></SidebarNavItem>
            <SidebarNavItem label="Trending" icon="fire"></SidebarNavItem>
            <SidebarNavItem label="Subscriptions" icon="collection"></SidebarNavItem>
        </ul>
    </SidebarSection>
    <SidebarSection>
        <ul>
            <SidebarNavItem label="Library" icon="duplicate"></SidebarNavItem>
            <SidebarNavItem label="History" icon="clock"></SidebarNavItem>
        </ul>
    </SidebarSection>
    <SidebarSection class="px-8 py-4 font-medium leading-5 border-b">
        <span class="text-sm">
            Sign in to like videos, comment, and subscribe.
        </span>
        <buttonLogin
            class="focus:outline-none flex items-center px-2 py-0.5 mt-3 text-sm text-blue-700 uppercase border border-blue-700 rounded-sm">
        </buttonLogin>
    </SidebarSection>
    <SidebarSection>
        <SidebarSectionHeading title="Best of YouTube"></SidebarSectionHeading>
        <ul>
            <SidebarNavItem label="Music" icon="musicNote"></SidebarNavItem>
            <SidebarNavItem label="Sports" icon="speakerphone"></SidebarNavItem>
            <SidebarNavItem label="Gaming" icon="puzzle"></SidebarNavItem>
            <SidebarNavItem label="Movies" icon="film"></SidebarNavItem>
            <SidebarNavItem label="News" icon="newspaper"></SidebarNavItem>
            <SidebarNavItem label="Live" icon="statusOnline"></SidebarNavItem>
            <SidebarNavItem label="360&deg; Video" icon="eye"></SidebarNavItem>
        </ul>
    </SidebarSection>
    <SidebarSection>
        <ul>
            <SidebarNavItem label="Browse channels" icon="plusCircle"></SidebarNavItem>
        </ul>
    </SidebarSection>
    <SidebarSection>
        <SidebarSectionHeading title="More from YouTube"></SidebarSectionHeading>
        <ul>
            <SidebarNavItem label="YouTube Premium" icon="play"></SidebarNavItem>
            <SidebarNavItem label="Live" icon="statusOnline"></SidebarNavItem>
        </ul>
    </SidebarSection>
    <SidebarSection>
        <ul>
            <SidebarNavItem label="Settings" icon="cog"></SidebarNavItem>
            <SidebarNavItem label="Report history" icon="flag"></SidebarNavItem>
            <SidebarNavItem label="Help" icon="questionMarkCircle"></SidebarNavItem>
            <SidebarNavItem label="Send feedback" icon="annotation"></SidebarNavItem>
        </ul>
    </SidebarSection>
    <SidebarSection class="px-6 py-4 text-xs font-semibold space-y-4">
        <TheFooter></TheFooter>
    </SidebarSection>
</template>

<script>
import ButtonLogin from './ButtonLogin.vue'
import SidebarSectionHeading from './SidebarSectionHeading.vue'
import SidebarNavItem from './SidebarNavItem.vue'
import SidebarSection from './SidebarSection.vue'
import TheFooter from './TheFooter.vue'

export default {
    components: {
        ButtonLogin,
        SidebarSectionHeading,
        SidebarNavItem,
        SidebarSection,
        TheFooter
    }
}
</script>