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
$ aws s3 cp C:/Users/pb25tik/Desktop/ICT-346_cloud/main.js s3://devopsteam06-i346 \
--profil devopsteam06
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
aws s3 ls s3://devopsteam06-i346 \
--profile devopsteam06-i346
```

```
[OUTPUT]
An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action

```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
aws cp create-repository \
--repository-name/
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
aws s3 ls s3://devopsteam06-i346 \
--profile devopsteam06-i346
//TODO
```

```
[OUTPUT]
//An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action
```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
 aws s3 ls s3://devopsteam06-i346/ \
--recursive
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
aws s3 ls s3://devopsteam06-i346 \
--profile devopsteam06-i346
```

```
[OUTPUT]
//An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action
```

* [La commande à réaliser pour effecuter l'action demandée]

```bash
//aws s3 sync /home/utilisateur/mon_repertoire s3://devopsteam-ict346/ \
--profile devopsteam6
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
aws s3 rm s3://devopsteam06-i346/main.js \
--profile devopsteam06-i346
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
//[OUTPUT]
//upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\HEAD to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/HEAD
upload: C:\Users\pb25tik\Desktop\ICT-346_cloud\I346-Leticia-Anthony\.git\ORIG_HEAD to s3://devopsteam06-i346/I346-Leticia-Anthony/.git/ORIG_HEAD

```

### Extraire uniquement les metadonnées d'un objet

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
//aws s3 ls s3://devopsteam06-i346 --profile devopsteam06-i346
```

```
[OUTPUT]
//An error occurred (AccessDenied) when calling the ListObjectsV2 operation: User: arn:aws:iam::709024702237:user/devopsteam06-i346 is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::devopsteam06-i346" because no identity-based policy allows the s3:ListBucket action
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

