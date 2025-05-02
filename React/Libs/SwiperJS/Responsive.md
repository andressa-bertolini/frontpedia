    import { useEffect, useState } from "react";
    import { Swiper, SwiperSlide } from "swiper/react";

    const [slidesPerView, setSlidesPerView] = useState(1);
    
    useEffect(() => {
        function handleResize(){
            if(window.innerWidth < 768){
                setSlidesPerView(1);
            }else{
                setSlidesPerView(1.5);
            }
        }

        handleResize();

        window.addEventListener("resize", handleResize);

        return () => {
            window.removeEventListener("resize", handleResize);
        }
    },[]);