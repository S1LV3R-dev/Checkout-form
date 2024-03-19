<script setup></script>

<template>
    <div class="order-image">
        <img />
    </div>
    <div class="order-info">
        <div class="order-title">
            <slot name="title"></slot>
        </div>
        <div class="order-description">
            <slot name="description"></slot>
        </div>
        <div class="order-price"><slot name="price"></slot> USD</div>
    </div>
    <div class="order-delete">
        <button>
            <svg xmlns="http://www.w3.org/2000/svg" width="15" height="15" viewBox="0 0 24 24">
                <path
                    d="M24 20.188l-8.315-8.209 8.2-8.282-3.697-3.697-8.212 8.318-8.31-8.203-3.666 3.666 8.321 8.24-8.206 8.313 3.666 3.666 8.237-8.318 8.285 8.203z"
                />
            </svg>
        </button>
    </div>
</template>
