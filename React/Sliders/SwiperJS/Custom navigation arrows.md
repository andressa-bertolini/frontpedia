import { Swiper, SwiperSlide } from 'swiper/react';
import { Navigation } from "swiper/modules";

import { useRef } from 'react';

const prevRef = useRef(null);
const nextRef = useRef(null);
const swiperRef = useRef(null);

useEffect(() => {
    if (swiperRef.current) {
        swiperRef.current.params.navigation.prevEl = prevRef.current;
        swiperRef.current.params.navigation.nextEl = nextRef.current;
        swiperRef.current.navigation.init();
        swiperRef.current.navigation.update();
    }
}, []);

          <Swiper
            modules={[Navigation]}
            navigation={{
              prevEl: prevRef.current,
              nextEl: nextRef.current,
            }}
            onBeforeInit={(swiper) => {
              swiper.params.navigation.prevEl = prevRef.current;
              swiper.params.navigation.nextEl = nextRef.current;
              swiper.navigation.init();
              swiper.navigation.update();
              swiperRef.current = swiper;
            }}
          >
            <SwiperSlide>
            </SwiperSlide>
        </Swiper>
        <div ref={prevRef} className="swiper-button-prev"></div>
        <div ref={nextRef} className="swiper-button-next"></div>
