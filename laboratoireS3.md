# Laboratoire S3

## Installation et configuration du CLI

* [Installer le client git](https://git-scm.com/)
  * Git bash vous embarque de nombreuses commandes Linux utiles pour s'entrainer avec S3 (cat, grep, touch, ls)
* [Installation du CLI - v2](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
* [Configuration du CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-quickstart.html#getting-started-quickstart-existing)
  * Les clés vous ont été partagées par oneDrive
* [Gestion des profiles](https://docs.aws.amazon.com/cli/v1/userguide/cli-configure-files.html#cli-configure-files-format-profile)
  * Vous devez créer un profile du nom de votre équipe et l'utiliser pour toute les futures commandes
  ```
  aws s3 <la commande> --profile devopsteam<xx>
  ```

## IAM Policy

Voici la "policy" qui vous a été attribuée:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "s3:ListAllMyBuckets",
            "Resource": "arn:aws:s3:::*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject",
                "s3:DeleteObject",
            ],
            "Resource": "arn:aws:s3:::devopsteam<XX>-i346/*" //XX -> devopsteam number
        }
    ]
}
```

## Exploiter un S3

Attention:
* Vous devez utiliser la v2 du CLI
* Le client offre soit la commande s3, soit s3api. En priorité vous devez essayer "s3".

### Créer un bucket

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* Le bucket existe-t-il ?
  oui 


```bash
aws s3 ls --profile devopsteam99-i346 | grep "devopsteam*"
```

```
[OUTPUT]
2025-01-27 22:23:30 devopsteam01-i346
2025-01-27 22:28:03 devopsteam02-i346
2025-01-27 22:28:05 devopsteam03-i346
2025-01-27 22:28:06 devopsteam04-i346
2025-01-27 22:28:08 devopsteam05-i346
2025-01-27 22:28:09 devopsteam06-i346
2025-01-27 22:28:11 devopsteam07-i346
2025-01-27 22:28:13 devopsteam08-i346
2025-01-27 22:28:14 devopsteam09-i346
2025-01-27 22:28:16 devopsteam10-i346
2025-02-03 19:32:33 devopsteam99-i346
```

* Créer un bucket (via un compte admin)

```bash
aws s3 mb s3://devopsteam99-i346 --region eu-central-1 --profile s3-admin
```

```
[OUTPUT]
make_bucket: devopsteam99-i346
```


### Uploader un fichier

//TODO en suivant le modèle livré sous "Créer un bucket"

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* [Vérifier l'état du bucket avant votre commande]

```bash
$ aws s3 ls s3://devopsteam06-i346 --profile devopsteam06-i346

```

```
[OUTPUT]
//TODO
An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action
```s

* [La commande à réaliser pour effecuter l'action demandée]

```bash
//TODO
$ aws s3 cp C:/Users/pb25tik/Desktop/ICT-346_cloud/main.js s3://devopsteam06-i346 --profil devopsteam06
```

```
[OUTPUT]
//TODO
upload: .\main.js to s3://devopsteam06-i346/main.js
```

### Uploader un répertoire

//TODO en suivant le modèle livré sous "Créer un bucket"

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* [Vérifier l'état du bucket avant votre commande]

```bash
aws s3 ls s3://devopsteam06-i346 --profile devopsteam06-i346
```

```
[OUTPUT]
An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action

```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
aws ecr create-repository --repository-name project-a/nginx-web-app
```

```
[OUTPUT]
//TODO
```

### Lister le contenu d'un "repertoire"

//TODO en suivant le modèle livré sous "Créer un bucket"

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* [Vérifier l'état du bucket avant votre commande]

```bash
aws s3 ls s3://devopsteam06-i346 --profile devopsteam06-i346
//TODO
```

```
[OUTPUT]
//An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action
```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
// aws s3 ls s3://devopsteam06-i346/ --recursive
```

```
[OUTPUT]
//An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action
```

### Synchroniser un répertoire local de sa machine avec un bucket

//TODO en suivant le modèle livré sous "Créer un bucket"

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* [Vérifier l'état du bucket avant votre commande]

```bash
aws s3 ls s3://devopsteam06-i346 --profile devopsteam06-i346
```

```
[OUTPUT]
//An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action
```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
//aws s3 sync /home/utilisateur/mon_repertoire s3://devopsteam-ict346/ --profile devopsteam6
```

```
[OUTPUT]
//upload: /home/utilisateur/mon_repertoire/fichier1.txt to s3://mon-bucket/fichier1.txt
upload: /home/utilisateur/mon_repertoire/fichier2.jpg to s3://mon-bucket/fichier2.jpg
upload: /home/utilisateur/mon_repertoire/dossier1/fichier3.png to s3://mon-bucket/dossier1/fichier3.png
```

### Publier un fichier présent sur un bucket en générant un lien (url) temporaire

//TODO en suivant le modèle livré sous "Créer un bucket"

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* [Vérifier l'état du bucket avant votre commande]

```bash
//TODO
```

```
[OUTPUT]
//TODO
```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
//TODO
```

```
[OUTPUT]
//TODO
```

### Supprimer un fichier

//TODO en suivant le modèle livré sous "Créer un bucket"

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* [Vérifier l'état du bucket avant votre commande]

```bash
//aws s3 ls s3://devopsteam06-i346 --profile devopsteam06-i346
```

```
[OUTPUT]
//An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action
```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
//aws s3 rm s3://devopsteam06-i346/main.js --profile devopsteam06-i346
```

```
[OUTPUT]
//delete: s3://devopsteam06-i346/main.js
```

### Vider un "repertoire"

//TODO en suivant le modèle livré sous "Créer un bucket"

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* [Vérifier l'état du bucket avant votre commande]

```bash
//aws s3 ls s3://devopsteam06-i346 --profile devopsteam06-i346
```

```
[OUTPUT]
//An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action
```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
//aws s3 cp C:/Users/pt57itt/Desktop/ICT-346_cloud/ s3://devopsteam06-i346 --recursive --profile devopsteam06-i346
```

```
[OUTPUT]
//upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\HEAD to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/HEAD
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\ORIG_HEAD to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/ORIG_HEAD
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\config to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/config
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\fsmonitor-watchman.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/fsmonitor-watchman.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\applypatch-msg.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/applypatch-msg.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\description to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/description
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\FETCH_HEAD to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/FETCH_HEAD
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\COMMIT_EDITMSG to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/COMMIT_EDITMSG
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\.MERGE_MSG.swp to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/.MERGE_MSG.swp
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\commit-msg.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/commit-msg.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\pre-push.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/pre-push.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\pre-commit.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/pre-commit.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\pre-receive.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/pre-receive.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\pre-applypatch.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/pre-applypatch.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\push-to-checkout.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/push-to-checkout.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\post-update.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/post-update.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\pre-merge-commit.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/pre-merge-commit.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\pre-rebase.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/pre-rebase.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\sendemail-validate.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/sendemail-validate.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\prepare-commit-msg.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/prepare-commit-msg.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\hooks\update.sample to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/hooks/update.sample
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\index to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/index
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\logs\HEAD to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/logs/HEAD
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\18\7404480a61def182bce453c5de326a6e902e8c to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/18/7404480a61def182bce453c5de326a6e902e8c
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\info\exclude to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/info/exclude
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\30\ce53d919e65a3305e83baffa8a6c473eb9f7cd to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/30/ce53d919e65a3305e83baffa8a6c473eb9f7cd
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\logs\refs\remotes\origin\HEAD to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/logs/refs/remotes/origin/HEAD
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\logs\refs\remotes\origin\main to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/logs/refs/remotes/origin/main
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\3a\4ad33bb036f5c48686fc62aff5636872004b74 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/3a/4ad33bb036f5c48686fc62aff5636872004b74
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\3b\287dd2e3390e1da7ed363c017cddbf7fd86aa9 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/3b/287dd2e3390e1da7ed363c017cddbf7fd86aa9
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\74\80b925c23ed09bb760f274d3aa2fe5b632257e to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/74/80b925c23ed09bb760f274d3aa2fe5b632257e
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\83\ae3e324fa87224c846e753252089ac08f3b73b to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/83/ae3e324fa87224c846e753252089ac08f3b73b
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\logs\refs\heads\main to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/logs/refs/heads/main
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\8b\7543b9e7a50aa41ff9602dd1a4694d7b55127c to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/8b/7543b9e7a50aa41ff9602dd1a4694d7b55127c
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\76\e40ce0bdb7b40f9e472242f77a698982466346 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/76/e40ce0bdb7b40f9e472242f77a698982466346
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\3c\8016edf0b10ca4cee2ac28b04067beaeae9c64 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/3c/8016edf0b10ca4cee2ac28b04067beaeae9c64
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\95\37bb9faef62bb8812e1e55d3c975556dbcb077 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/95/37bb9faef62bb8812e1e55d3c975556dbcb077
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\af\ffe8a58d24ebb38e1744f65362b3445cf8631d to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/af/ffe8a58d24ebb38e1744f65362b3445cf8631d
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\bc\2cd444ed0de2fb96d28cc78585ec1743d1cf64 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/bc/2cd444ed0de2fb96d28cc78585ec1743d1cf64
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\b8\ade88c859115d16fe233ffcce3b9d67a358595 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/b8/ade88c859115d16fe233ffcce3b9d67a358595
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\c2\6db8be641c03434c3d615341024798744df29d to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/c2/6db8be641c03434c3d615341024798744df29d
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\d0\727915c2bef595cd6a39a3f86a30cca42d9c02 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/d0/727915c2bef595cd6a39a3f86a30cca42d9c02
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\d0\bc9a1aa776c4f6b9357bd321042eccbfddcdaf to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/d0/bc9a1aa776c4f6b9357bd321042eccbfddcdaf
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\d3\e7d5e1d3e8a0c471ec999ae3421484546773ab to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/d3/e7d5e1d3e8a0c471ec999ae3421484546773ab
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\eb\a0793b66d9a2b259f5ee7ccd981fca7c5a6b86 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/eb/a0793b66d9a2b259f5ee7ccd981fca7c5a6b86
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\f1\6ced8ad11c8914c3206e68e7353a6d67af2d40 to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/f1/6ced8ad11c8914c3206e68e7353a6d67af2d40
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\pack\pack-e0c34756a936d6b1eb565b8fa2243803f199dd69.rev to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/pack/pack-e0c34756a936d6b1eb565b8fa2243803f199dd69.rev
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\packed-refs to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/packed-refs
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\pack\pack-e0c34756a936d6b1eb565b8fa2243803f199dd69.pack to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/pack/pack-e0c34756a936d6b1eb565b8fa2243803f199dd69.pack
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\ff\3c3a540d95bf9f628b03dc364945cfd242bd1a to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/ff/3c3a540d95bf9f628b03dc364945cfd242bd1a
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\refs\heads\main to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/refs/heads/main
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\refs\remotes\origin\HEAD to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/refs/remotes/origin/HEAD
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\refs\remotes\origin\main to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/refs/remotes/origin/main
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\pack\pack-e0c34756a936d6b1eb565b8fa2243803f199dd69.idx to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/pack/pack-e0c34756a936d6b1eb565b8fa2243803f199dd69.idx
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\README.md to s3://devopsteam06-i346/I346-Leticia-Anthony/README.md
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\main.js to s3://devopsteam06-i346/main.js
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\objects\e2\f5d5302622554838f0c1eeeb9f3d1934d3939a to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/objects/e2/f5d5302622554838f0c1eeeb9f3d1934d3939a
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\laboratoireS3.md to s3://devopsteam06-i346/I346-Leticia-Anthony/laboratoireS3.md

```

### Extraire uniquement les metadonnées d'un objet

//TODO en suivant le modèle livré sous "Créer un bucket"

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* [Vérifier l'état du bucket avant votre commande]

```bash
//TODO
```

```
[OUTPUT]
//TODO
```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
//TODO
```

```
[OUTPUT]
//TODO
```

### Vider le bucket

//TODO en suivant le modèle livré sous "Créer un bucket"

* [AWS Official Doc - Create Bucket](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/s3/mb.html#examples)

* [Vérifier l'état du bucket avant votre commande]

```bash
//TODO
```

```
[OUTPUT]
//TODO
```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
//TODO
```

```
[OUTPUT]
//TODO
```

---

## Questions d'analyse

Consigne : répondre en utilisant des sources officielles et en vous appuyant dessus pour répondre.

### Pourquoi est-il déconseillé de détruire un bucket S3 selon AWS ?

* [Sources AWS : https://docs.aws.amazon.com/AmazonS3/latest/userguide/delete-bucket.html]
 

[Car si on a des données lier a des applications ca peut les endommager et perdre toutes les donées]

### Quelle est la différence entre un Bucket S3 et Glacier ?

* [Sources AWS : https://managedserver.fr/aws-s3-e-aws-glacier-quali-sono-le-differenze/ ]

[Un bucket S3 est conçu pour le stockage de données fréquemment accessibles avec une latence faible, tandis que Glacier est destiné à l'archivage de données à long terme, offrant un stockage moins coûteux mais avec des délais de récupération plus longs.]

### Reprenez l'IAM "Policy" et expliquer ce que vous pouvez en déduire au niveau des droits qui vous sont alloués

Consigne : Reprenez la "policy" et documenter chaque ligne

Vesrion : ca nous donne la version.
Statement: on initiale une condition avec un tableau.
Effect : ça autorise les paramtères que on a le droit de faire.
Action : Autorise l'utilisateur à voir tous les buckets S3 qu'il possède.
Ressource : c'est la règle qui s'applique au objet S3

Effect : ça autorise les paramtères que on a le droit de faire.
Action : un tableau avec les droits que nous pouvons faire ( putobject, getobjetc, deleteobject)
Ressource : 

