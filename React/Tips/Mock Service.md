## Mock Service

```
import { createAsyncThunk } from '@reduxjs/toolkit';
import { navigationApi, processingApi } from '@services/index';
import getEnvironmentConfig from '@utils/environments';
import { properties } from '../properties.types';

const environments = getEnvironmentConfig(import.meta.env.VITE_APP_ENV);

if (typeof environments === 'string') {
  throw new Error(`Ambiente inválido: ${import.meta.env.VITE_APP_ENV}`);
}

const NAV_API_URL = `${environments.navigation}/properties`;
const PROCESS_API_URL = `${environments.processing}/properties`;

const apiRequest = async (
  api: typeof navigationApi | typeof processingApi,
  url: string,
  method: 'get' | 'post' | 'put' | 'delete',
  data?: any,
) => {
  try {
    const response = await api({ method, url, data });
    return response.data;
  } catch (error) {
    console.error(`Erro ao realizar a requisição: ${error}`);
    throw error;
  }
};

{
  /*export const fetchProperties = createAsyncThunk<
  { properties: Properties[]; totalPages: number; totalItems: number },
  { page?: number; pageSize?: number; [key: string]: any }
>('properties/fetchProperties', async (params) => {
  const { page = 1, pageSize, ...filters } = params;

  const query = new URLSearchParams({ page: String(page), pageSize: String(pageSize), ...filters });

  const data = await apiRequest(navigationApi, `${NAV_API_URL}?${query.toString()}`, 'get');

  return { properties: data.content, totalPages: data.totalPages, totalItems: data.totalItems };
});*/
}

export const fetchProperties = createAsyncThunk<
  { properties: Properties[]; totalPages: number; totalItems: number },
  { page?: number; pageSize?: number; [key: string]: any }
>('properties/fetchProperties', async () => {
  const mockData = {
    success: true,
    content: [
      {
        "id": 1,
        "title": "Modern Downtown Condo with Skyline Views",
        "description": "Lorem Ipsum Dolor Sit Amet",
        "purpose": "rent",
        "type": "apartment",
        "price": 3200,
        "area": 1023,
        "bedrooms": 2,
        "bathrooms": 2,
        "city": "New York City",
        "state": "New York",
        "featuredImage": "https://andressabertolini.com/project/prime-estate/mock/images/property-1-1.png",
        "images": [
          "https://andressabertolini.com/project/prime-estate/mock/images/property-1-1.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-1-2.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-1-3.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-1-4.png"
        ],
        "amenities": [
          "Furnished","Parking Spaces","Centrally Air-Conditioned","Gym or Health Club", "Swimming Pool", "Laundry Facility", "View", "Elevators in Building", "Business Center"
        ]
      },
      {
        "id": 2,
        "title": "Spacious Family Home with Large Backyard",
        "description": "Lorem Ipsum Dolor Sit Amet",
        "purpose": "sale",
        "type": "house",
        "price": 480000,
        "area": 2260,
        "bedrooms": 4,
        "bathrooms": 3,
        "city": "Dallas",
        "state": "Texas",
        "featuredImage": "https://andressabertolini.com/project/prime-estate/mock/images/property-2-1.png",
        "images": [
          "https://andressabertolini.com/project/prime-estate/mock/images/property-2-1.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-2-2.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-2-3.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-2-4.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-2-5.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-2-6.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-2-7.png"
        ],
        "amenities": [
          "Furnished","Parking Spaces","Centrally Air-Conditioned","Gym or Health Club", "Swimming Pool", "Laundry Facility", "View", "Elevators in Building", "Business Center"
        ]
      },
      {
        "id": 3,
        "title": "Elegant Suburban Retreat",
        "description": "Lorem Ipsum Dolor Sit Amet",
        "purpose": "sale",
        "type": "house",
        "price": 520000,
        "area": 1938,
        "bedrooms": 3,
        "bathrooms": 2,
        "city": "Phoenix",
        "featuredImage": "https://andressabertolini.com/project/prime-estate/mock/images/property-3-1.png",
        "images": [
          "https://andressabertolini.com/project/prime-estate/mock/images/property-3-1.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-3-2.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-3-3.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-3-4.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-3-5.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-3-6.png",
          "https://andressabertolini.com/project/prime-estate/mock/images/property-3-7.png"
        ],
        "amenities": [
          "Furnished","Parking Spaces","Centrally Air-Conditioned","Gym or Health Club", "Swimming Pool", "Laundry Facility", "View", "Elevators in Building", "Business Center"
        ]
      },
    ],
    totalItems: 7,
    totalPages: 1,
    currentPage: 1,
    isLastPage: true,
  };

  return {
    properties: mockData.content,
    totalPages: mockData.totalPages,
    totalItems: mockData.totalItems,
  };
});

```