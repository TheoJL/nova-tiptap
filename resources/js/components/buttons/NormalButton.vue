<template>
    <button
        type="button"
        class="
            btn
            btn-default
            p-2
            leading-none
            text-xs
            min-w-8
            h-8
            tiptap-button
        "
        :class="[
            (buttonKey == 'bold' && isActive.bold() ? 'btn-primary' : ''),
            (buttonKey == 'italic' && isActive.italic() ? 'btn-primary' : ''),
            (buttonKey == 'code' && isActive.code() ? 'btn-primary' : ''),
            (buttonKey == 'bullet_list' && isActive.bullet_list() ? 'btn-primary' : ''),
            (buttonKey == 'ordered_list' && isActive.ordered_list() ? 'btn-primary' : ''),
            (buttonKey == 'code_block' && isActive.code_block() ? 'btn-primary' : ''),
            (buttonKey == 'blockquote' && isActive.blockquote() ? 'btn-primary' : ''),
            'is-' + buttonKey

        ]"
        @click="commands[buttonKey]"
    >
        <font-awesome-icon v-if="buttonKey == 'bullet_list'" :icon="['far', 'list-ul']">
        </font-awesome-icon>

        <font-awesome-icon v-if="buttonKey == 'ordered_list'" :icon="['far', 'list-ol']">
        </font-awesome-icon>

        <font-awesome-icon v-if="buttonKey == 'blockquote'" :icon="['far', 'quote-right']">
        </font-awesome-icon>
    </button>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";

import {
    faFileCode,
    faListAlt,
    faCommentDots
} from "@fortawesome/free-regular-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

library.add(faFileCode, faListAlt, faListAlt, faCommentDots);

export default {
    props: ["buttonKey", "isActive", "commands"],

    components: {
        FontAwesomeIcon
    }
};
</script>
