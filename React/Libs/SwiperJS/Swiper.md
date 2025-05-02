## Swiper

**Installation**
```
npm install swiper
```

**index.js**
```
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import 'swiper/css/scrollbar';
```

**Swiper.jsx**
```
import { Swiper, SwiperSlide } from 'swiper/react';

<Swiper
    slidesPerView=1
    pagination={{clickable: true}}
    navigation
>
    <SwiperSlide>
        <img
            src="url"
            alt="Text"
            className="slide"
        />
    </SwiperSlide>
    <SwiperSlide>
        <img
            src="url"
            alt="Text"
            className="slide"
        />
    </SwiperSlide>
</Swiper>
```

Option using map
```
const data = {
    {id: '1', image: 'url1'},
    {id: '2', image: 'url2'}
}

<Swiper
    slidesPerView=1
    pagination={{clickable: true}}
    navigation
>
    {data.map((item) => (
        <SwiperSlide key="item.id">
            <img
                src="url"
                alt="Text"
                className="slide"
            />
        </SwiperSlide>
    ))}
</Swiper>
```