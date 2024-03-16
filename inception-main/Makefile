# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: abalhamm <abalhamm@student.42.fr>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2024/03/16 14:58:35 by abalhamm          #+#    #+#              #
#    Updated: 2024/03/16 14:58:36 by abalhamm         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

all: build up

up:
	cd srcs && docker compose up -d

down:
	cd srcs && docker compose down

build:
	if [ ! -d "/home/${USER}/data" ]; then \
		mkdir -p "/home/${USER}/data/wp" \
		mkdir -p "/home/${USER}/data/db"; \
	fi
	cd srcs && docker compose build

logs:
	cd srcs && docker compose logs -f

remove_volumes:
	docker volume rm $$(docker volume ls -q)
	sudo rm -rf /home/${USER}/data

fclean: down remove_volumes
	docker system prune --all --force
	@if [ ! -z "$(docker images -q)" ]; then \
		docker rmi -f $$(docker images -q); \
	fi

re: fclean all
