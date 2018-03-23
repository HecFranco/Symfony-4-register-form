# RESUMEN DE COMANDOS CONSOLA UTILIZADOS

## COMPONENTES SYMFONY
* Componente Servidor, `composer require server --dev`
* Componente Twig, `composer require twig`
* Componente Doctrine, `composer require doctrine maker`
* Componente Form, `composer require form`
* Componente Security, `composer require security`
* Componente Validator, `composer require validator`
* Componente Validator, `composer require symfony/validator`

# GESTIÓN DE BASE DE DATOS
php bin/console doctrine:database:create
php bin/console doctrine:database:drop --force
php bin/console doctrine:schema:update --force
php bin/console doctrine:migrations:diff
php bin/console doctrine:migrations:migrate

_[config/packages/doctrine.yaml](config/packages/doctrine.yaml)

```yaml
# config/packages/doctrine.yaml
        mappings:
            App:
                is_bundle: false
                # type: annotation
                type: yml
                # dir: '%kernel.project_dir%/src/Entity'
                dir: '%kernel.project_dir%/config/doctrine'
                prefix: 'App\Entity'
                alias: App
```

_[config/routes.yaml](config/routes.yaml)
```yaml
# Importante en los archivos con extensión .yaml cada sangrado equivale a 4 espacios!!!
routing_distributed:
    # loads routes from the given routing file stored in some bundle
    resource: '..\src\Resources\config\routing.yaml' 
    type: yml
```

_[config/validator/validation.yaml](config/validator/validation.yaml)
```yaml
App\Entity\User:
  constraints:
      - Symfony\Bridge\Doctrine\Validator\Constraints\UniqueEntity: email
  properties:
      email:
          - Email: ~
```