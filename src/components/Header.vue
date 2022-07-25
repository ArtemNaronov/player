<template>
    <header>
        <div class="container">
            <div class="logo">
                <img src="../assets/logo.svg" alt="">
            </div>
            <nav>
                <ul>
                    <li>Каталог</li>
                    <li>Рекомендации</li>
                    <li>Моя музыка</li>
                    <li>Радио</li>
                </ul>
            </nav>
            <div class="search">
                <span></span>
            </div>
        </div>        
    </header>
</template>

<style lang="scss" scoped>
    header {
        width: 100vw;
        height: 60px;
        background: #007AFF;
        & div {
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: space-between;
            
            & ul {
                display: flex;

                & li {
                    list-style: none;
                    padding: 20px;
                    color: #FFFFFF;
                    cursor: pointer;
                }
            }

            & .search span {
                background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='24' height='24' viewBox='0 0 24 24' fill='none'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M16.1501 14.3889H15.2192L14.8955 14.0677C16.0388 12.7345 16.7341 11.0062 16.7341 9.1126C16.7341 4.90325 13.322 1.49121 9.11266 1.49121C4.90331 1.49121 1.49127 4.90325 1.49127 9.1126C1.49127 13.322 4.90331 16.734 9.11266 16.734C11.0063 16.734 12.7334 16.0399 14.0666 14.8978L14.3902 15.2191V16.1477L20.2504 21.9998L21.9987 20.2516L16.1501 14.3889ZM9.11266 14.389C6.19777 14.389 3.83632 12.0275 3.83632 9.1126C3.83632 6.19889 6.19777 3.83625 9.11266 3.83625C12.0264 3.83625 14.389 6.19889 14.389 9.1126C14.389 12.0275 12.0264 14.389 9.11266 14.389Z' fill='white'/%3E%3C/svg%3E");
                display: block;
                width:24px;
                height: 24px;
                cursor: pointer;
            }
        }
       
    }
</style>