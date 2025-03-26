/services/api/

ApiConfig.ts
```
import axios from "axios"

export const Api = () => {
  return axios.create({
    baseURL: 'http://localhost:3333'
  });
};
```

ApiException.ts
```
export class ApiException extends Error {
  public readonly message: string = '';

  constructor(message: string) {
    super();

    this.message = message;
  }
}
```

/tasks (example)
TasksService.ts
```
import { ApiException } from "../ApiException";
import { Api } from "../ApiConfig";

export interface ITasks {
  id: number;
  title: string;
  isCompleted: boolean;
}

const getAll = async (): Promise<ITasks[] | ApiException> => {
  try {
    const { data } = await Api().get('/tasks');
    return data;
  } catch (error: any) {
    return new ApiException(error.message || 'Error.');
  }
};

const getById = async (id: number): Promise<ITask | ApiException> => {
  try {
    const { data } = await Api().get(`/tasks/${id}`);
    return data;
  } catch (error: any) {
    return new ApiException(error.message || 'Error.');
  }
};

const create = async (dataToCreate: Omit<ITask, 'id'>): Promise<ITask | ApiException> => {
  try {
    const { data } = await Api().post<any>('/tasks', dataToCreate);
    return data;
  } catch (error: any) {
    return new ApiException(error.message || 'Erro ao criar o registro.');
  }
};

const updateById = async (id: number, dataToUpdate: ITask): Promise<ITask | ApiException> => {
  try {
    const { data } = await Api().put(`/tasks/${id}`, dataToUpdate);
    return data;
  } catch (error: any) {
    return new ApiException(error.message || 'Error.');
  }
};

const deleteById = async (id: number): Promise<undefined | ApiException> => {
  try {
    await Api().delete(`/tasks/${id}`);
    return undefined;
  } catch (error: any) {
    return new ApiException(error.message || 'Error.');
  }
};

export const TasksService = {
  getAll,
  create,
  getById,
  updateById,
  deleteById,
};
```