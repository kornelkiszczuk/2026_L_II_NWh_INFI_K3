# Simple Flask App

Aplikacja Dydaktyczna wyswietlajaca imie i wiadomosc w roznych formatach dla zajec
o Continuous Integration, Continuous Delivery i Continuous Deployment.

- W projekcie wykorzystamy virtual environment, dla utworzenia hermetycznego srodowiska dla aplikacji:

  ```
  # tworzymy hermetyczne srodowisko dla bibliotek aplikacji:
  $ python -m venv .venv

  # aktywowanie hermetycznego srodowiska
  $ source .venv/bin/activate
  $ pip install -r requirements.txt
  $ pip install -r test_requirements.txt

  # zobacz
  $ pip list
  ```

  Sprawdz: [tutorial venv](https://docs.python.org/3/tutorial/venv.html) oraz [biblioteki flask](http://flask.pocoo.org).

- Uruchamianie applikacji:

  ```
  # jako zwykly program
  $ python main.py

  # albo:
  $ PYTHONPATH=. FLASK_APP=hello_world flask run
  ```

- Uruchamianie testow (see: http://doc.pytest.org/en/latest/capture.html):

  ```
  $ PYTHONPATH=. py.test
  $ PYTHONPATH=. py.test --verbose -s
  ```

- Kontynuujac prace z projektem, aktywowanie hermetycznego srodowiska dla aplikacji py:

  ```
  # deaktywacja
  $ deactivate
  ```

  ```
  ...

  # aktywacja
  $ source .venv/bin/activate
  ```

- Single point of entry (Makefile):

  ```
  $ make deps
  $ make lint
  $ make test
  $ make run
  $ make docker_build
  $ make docker_run
  $ make docker_push
  ```

- Integracja z CircleCI: konfiguracja w `.circleci/config.yml` (workflow `build-and-test`:
  deps, lint, test, docker_build, docker_push).

# Pomocnicze

## Ubuntu

- Instalacja dockera: [dockerce howto](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

## Centos

- Instalacja docker-a:

  ```
  $ yum remove docker \
        docker-common \
        container-selinux \
        docker-selinux \
        docker-engine

  $ yum install -y yum-utils

  $ yum-config-manager \
      --add-repo \
      https://download.docker.com/linux/centos/docker-ce.repo

  $ yum makecache fast
  $ yum install -y docker-ce
  $ systemctl start docker
  ```
