import { Swiper, SwiperSlide } from 'swiper/react';
import { Mousewheel } from "swiper/modules";

<Swiper
    direction="vertical"
    slidesPerView={1}
    style={{ height: "100%" }}
    modules={[Mousewheel]}
    mousewheel={{ forceToAxis: true }}
    >
    <SwiperSlide>
    </SwiperSlide>
</Swiper>