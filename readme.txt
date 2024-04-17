Vytvořte dle prototypu návrh. Kategorie nad produkty musí být vytvořeny tak, že budou řešeny pomocí overflow scroll a v případě, že přesahují přes okraj obrazovky, tak se zobrazí šipky, které posunou overflow  scroll na další kategorii ( viz. script níže ).

Desktop řešit nemusíte, případně jen vhodně zalomte. Preferované zobrazení produktů je pomocí gridu.

Menu nemusí být funkční, ani košík. Mělo by to zabrat max 1 hodinu.  Pokud by vám to mělo zabrat více času, tak pošlete co jste zvládli do hodiny.

Použijte :

- Tailwind

- React query ( doporučeno, není nutné )

- Next.js

Api pro jídlo: https://661ed74316358961cd92f0a0.mockapi.io/meals

Api pro kategorie: https://661ed74316358961cd92f0a0.mockapi.io/categories

Design: https://www.figma.com/proto/2Sg5G2DS18S9LkAwFsNahK/Untitled?page-id=0%3A1&type=design&node-id=0-76&viewport=553%2C419%2C0.87&t=OrwZbZeyJjGtzVoX-1&scaling=min-zoom&mode=design

script pro overflow scroll:

                        (()=> {

                            const scrollElement = document.querySelector("#tab-1 .c-section__slider")
                            const chevronRight = document.querySelector("#tab-1 .chevron-right")
                            const chevronLeft = document.querySelector("#tab-1 .chevron-left")

                            const initScroll = () => {
                                var scrollWidth = scrollElement.scrollWidth;
                                var scrollLeft = scrollElement.scrollLeft;
                                var offsetWidth = scrollElement.offsetWidth;

                                if (scrollLeft == 0) {
                                    chevronLeft.classList.add('hidden')
                                } else {
                                    chevronLeft.classList.remove('hidden')
                                }
                                if ((scrollLeft + offsetWidth) >= scrollWidth) {
                                    chevronRight.classList.add('hidden')
                                } else {
                                    chevronRight.classList.remove('hidden')
                                }
                            }


                            chevronRight.addEventListener('click', (e) => {
                                scrollElement.scrollTo({
                                    left: scrollElement.offsetWidth + scrollElement.scrollLeft,
                                    behavior: 'smooth'
                                })
                            })

                            chevronLeft.addEventListener('click', (e) => {
                                scrollElement.scrollTo({
                                    left: -1 * scrollElement.offsetWidth + scrollElement.scrollLeft,
                                    behavior: 'smooth'
                                })
                            })


                            scrollElement.addEventListener('scroll', (e) => {
                                initScroll()
                            })
                            window.addEventListener('resize', (e) => {
                                initScroll()
                            })
                            initScroll()
                        })()
