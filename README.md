Symfony2 PHP CodeSniffer Coding Standard
========================================

A code standard to check against the [Symfony coding standards](http://symfony.com/doc/current/contributing/code/standards.html)

Installation for Symfony using Composer
---------------------------------------

1. Update composer.json

```json
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/paza/Symfony2-coding-standard"
        }
    ],
    "require-dev": {
        "paza/symfony2-coding-standard": "dev-master",
    },
    "scripts": {
        "post-install-cmd": [
            "rm -rf vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/Symfony2 && cp -R vendor/paza/Symfony2-coding-standard vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/Symfony2",
            "./bin/phpcs --config-set default_standard Symfony2"
        ],
        "post-update-cmd": [
            "rm -rf vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/Symfony2 && cp -R vendor/paza/Symfony2-coding-standard vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/Symfony2",
            "./bin/phpcs --config-set default_standard Symfony2"
        ]
    },
```

2. Update vendors

    composer update paza/symfony2-coding-standard

3. Install pre-commit hook (optional)

Extend your composer.json with the following params...

```json
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/paza/git-hooks"
        }
    ],
    "require-dev": {
        "paza/git-hooks": "dev-master",
    },
    "scripts": {
        "post-install-cmd": [
            "cp vendor/paza/git-hooks/phpcs-pre-commit/pre-commit .git/hooks/pre-commit"
        ],
        "post-update-cmd": [
            "cp vendor/paza/git-hooks/phpcs-pre-commit/pre-commit .git/hooks/pre-commit"
        ]
    },
```

4. Use it!

        ./bin/phpcs
        ./bin/phpcs src/