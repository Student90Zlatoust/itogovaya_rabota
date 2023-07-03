# itogovaya_rabota
import requests

proxies = {
    "http": "http://localhost:8866",
    "https": "https://localhost:8866",
}

def get_pokemon_info(name):
    try:
        response = requests.get(f'https://pokeapi.co/api/v2/pokemon/{name}', verify=False)
        response.raise_for_status()

        pokemon_info = response.json()
        print(f'Покемон:{name}')
        print(f'Вес {pokemon_info ["weight"]}')
        print(f'Рост {pokemon_info ["weight"]}')
        print(f'Таланты {pokemon_info ["weight"]}')
        print(f'Вид {pokemon_info ["weight"]}')
        

        return pokemon_info

    except requests.exceptions.NTTPError as err:
        print(f'Ошибка: {err}')
        return None


name = input('Введите название покемона: ')
get_pokemon_info(name)
