<template>
    <div class="contact-item" @click="goUserProfile(contact.username)">
        <div class="avatar">
            <n-avatar size="large" :src="contact.avatar" />
        </div>
        <div class="base-info">
            <div class="username">
                <strong>{{ contact.nickname }}</strong>
                <span> @{{ contact.username }} </span>
            </div>
            <div class="uid">UID. {{ contact.user_id }}</div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router';
const router = useRouter();

const props = withDefaults(defineProps<{
    contact: Item.ContactItemProps
}>(), {})
const goUserProfile = (username: string) => {
    router.push({
        name: 'user',
        query: { username: username },
    });
};
</script>

<style lang="less" scoped>
.contact-item {
    display: flex;
    width: 100%;
    padding-left: 16px;
    padding-right: 16px;
    padding-top: 12px;
    padding-bottom: 12px;

    &:hover {
        background: #f7f9f9;
        cursor: pointer;
    }

    .avatar {
        width: 55px;
    }

    .base-info {
        position: relative;
        width: calc(100% - 55px);

        .username {
            line-height: 16px;
            font-size: 16px;
        }

        .uid {
            font-size: 14px;
            line-height: 14px;
            margin-top: 10px;
            opacity: 0.75;
        }
    }
}

.dark {
    .contact-item {
        &:hover {
            background: #18181c;
        }
        background-color: rgba(16, 16, 20, 0.75);
    }
}
</style>