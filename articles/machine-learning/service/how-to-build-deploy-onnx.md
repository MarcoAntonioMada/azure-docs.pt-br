---
title: Criar e implantar modelos ONNX interoperáveis
titleSuffix: Azure Machine Learning service
description: Saiba mais sobre o ONNX e como usar o Azure Machine Learning para criar e implantar modelos do ONNX
services: machine-learning
ms.service: machine-learning
ms.component: core
ms.topic: conceptual
ms.reviewer: jmartens
ms.author: prasantp
author: prasanthpul
ms.date: 09/24/2018
ms.custom: seodec18
ms.openlocfilehash: 15aa80c5291854c937bdc128a597ed5bebd608a2
ms.sourcegitcommit: c2e61b62f218830dd9076d9abc1bbcb42180b3a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53437411"
---
# <a name="onnx-and-azure-machine-learning-create-and-deploy-interoperable-ai-models"></a>ONNX e Azure Machine Learning: Criar e implantar modelos de AI interoperáveis

O formato ONNX [(Open Neural Network Exchange)](https://onnx.ai) é um padrão aberto para representar modelos de machine learning. O ONNX tem o suporte de uma [comunidade de parceiros](https://onnx.ai/supported-tools), incluindo a Microsoft, que criam ferramentas e estruturas compatíveis. A Microsoft está comprometida com uma IA aberta e interoperável para que os desenvolvedores e cientistas de dados possam:

+ Usar a estrutura preferida para criar e treinar modelos
+ Implantar modelos de multiplataforma com trabalho de integração mínimo

A Microsoft dá suporte ao ONNX em todos os seus produtos, incluindo o Azure e o Windows, a fim de ajudar você a atingir essas metas.  

## <a name="why-choose-onnx"></a>Por que escolher o ONNX?
A interoperabilidade do ONNX permite colocar ótimas ideias em produção mais rápido. Com ONNX, cientistas de dados podem escolher sua estrutura preferencial para o trabalho. Da mesma forma, os desenvolvedores podem gastar menos tempo preparando modelos para produção e implantar na nuvem e na borda.  

Você pode criar modelos ONNX a partir de várias estruturas, incluindo PyTorch, Chainer, Kit de Ferramentas Cognitivas Microsoft (CNTK), MXNet, ML.Net, TensorFlow, Keras, SciKit-Learn e muito mais.

Também há um ecossistema de ferramentas para visualizar e acelerar modelos ONNX. Uma série de modelos ONNX pré-treinados também está disponível para cenários comuns.

Os [modelos ONNX podem ser implantados](#deploy) na nuvem usando o Azure Machine Learning e ONNX Runtime. Eles também podem ser implantados em dispositivos Windows 10 usando o [ML do Windows](https://docs.microsoft.com/windows/ai/). Podem até mesmo ser implantados em outras plataformas usando conversores disponíveis na comunidade ONNX. 

[ ![Diagrama de fluxo do ONNX mostrando o treinamento, os conversores e a implantação](media/concept-onnx/onnx.png) ] (./media/concept-onnx/onnx.png#lightbox)

## <a name="get-onnx-models"></a>Obter modelos ONNX

Você pode obter modelos ONNX de várias maneiras:
+ Obtenha um modelo ONNX pré-treinado do [ONNX Model Zoo](https://github.com/onnx/models) (veja o exemplo na parte inferior deste artigo)
+ Gerar um modelo ONNX personalizado do [Serviço de Visão Personalizada do Azure](https://docs.microsoft.com/azure/cognitive-services/Custom-Vision-Service/) 
+ Converter modelo existente de outro formato para ONNX (veja o exemplo na parte inferior deste artigo) 
+ Treinar um novo modelo ONNX no serviço Aprendizado de Máquina do Azure (consulte o exemplo na parte inferior deste artigo)

## <a name="saveconvert-your-models-to-onnx"></a>Salvar/converter seus modelos ONNX

Você pode converter modelos existentes em ONNX ou salvá-los como ONNX no final do seu treinamento.

|Estrutura para modelo|Exemplo de conversão ou ferramenta|
|-----|-------|
|PyTorch|[Bloco de anotações do Jupyter](https://github.com/onnx/tutorials/blob/master/tutorials/PytorchOnnxExport.ipynb)|
|CNTK (Microsoft&nbsp;Cognitive&nbsp;Toolkit&nbsp;)|[Bloco de anotações do Jupyter](https://github.com/onnx/tutorials/blob/master/tutorials/CntkOnnxExport.ipynb)|
|TensorFlow|[conversor tensorflow-onnx](https://github.com/onnx/tensorflow-onnx)|
|Encadeador|[Bloco de anotações do Jupyter](https://github.com/onnx/tutorials/blob/master/tutorials/ChainerOnnxExport.ipynb)|
|MXNet|[Bloco de anotações do Jupyter](https://github.com/onnx/tutorials/blob/master/tutorials/MXNetONNXExport.ipynb)|
|Keras, ScitKit-Learn, CoreML<br/>XGBoost e libSVM|[WinMLTools](https://docs.microsoft.com/windows/ai/convert-model-winmltools)|

É possível encontrar a lista mais recente de estruturas e conversores compatíveis no [site de tutoriais do ONNX](https://github.com/onnx/tutorials).

<a name="deploy"></a>

## <a name="deploy-onnx-models-in-azure"></a>Implantar modelos do ONNX no Azure

Com o serviço do Azure Machine Learning, é possível implantar, gerenciar e monitorar os modelos do ONNX. Usando o [fluxo de trabalho de implantação](concept-model-management-and-deployment.md) padrão e o ONNX Runtime, é possível criar um ponto de extremidade REST hospedado na nuvem. Confira um exemplo completo do Jupyter Notebook no final deste artigo e experimente-o. 

### <a name="install-and-configure-onnx-runtime"></a>Instalar e configurar o ONNX Runtime

ONNX Runtime é um mecanismo de inferência de alto desempenho para modelos ONNX. Ele fornece aceleração de hardware tanto em CPU como em GPU, com APIs disponíveis para Python, C# e C. O ONNX Runtime dá suporte a modelos ONNX 1.2+ e executa no Linux, Windows e Mac. Pacotes do Python estão disponíveis em [PyPi.org](https://pypi.org) ([CPU](https://pypi.org/project/onnxruntime), [GPU](https://pypi.org/project/onnxruntime-gpu)) e o [pacote C#](https://www.nuget.org/packages/Microsoft.ML.OnnxRuntime/) está em [Nuget.org](https://www.nuget.org). Saiba mais sobre o projeto no [GitHub](https://github.com/Microsoft/onnxruntime). 

Para instalar o ONNX Runtime para Python, use:
```python
pip install onnxruntime
```

Para chamar o ONNX Runtime no script do Python, use:
```python
import onnxruntime

session = onnxruntime.InferenceSession("path to model")
```

A documentação que acompanha o modelo geralmente informa as entradas e saídas para usar o modelo. Também é possível usar uma ferramenta de visualização como o [Netron](https://github.com/lutzroeder/Netron) para exibir o modelo. O ONNX Runtime também permite consultar os metadados do modelo, as entradas e as saídas:
```python
session.get_modelmeta()
first_input_name = session.get_inputs()[0].name
first_output_name = session.get_outputs()[0].name
```

Para fazer inferências no modelo, use `run` e passe a lista de saídas que deseja receber (deixe em branco se quiser todas) e um mapa dos valores de entrada. O resultado é uma lista das saídas.
```python
results = session.run(["output1", "output2"], {"input1": indata1, "input2": indata2})
results = session.run([], {"input1": indata1, "input2": indata2})
```

Para obter a referência completa da API do Python, consulte os [documentos de referência do ONNX Runtime](https://aka.ms/onnxruntime-python).

### <a name="example-deployment-steps"></a>Exemplo de etapas de implantação

Confira um exemplo de como implantar um modelo ONNX:

1. Inicialize seu espaço de trabalho do serviço de Aprendizado de Máquina do Azure. Se você ainda não tiver um, saiba como criar um workspace [neste guia de início rápido](quickstart-get-started.md).

   ```python
   from azureml.core import Workspace

   ws = Workspace.from_config()
   print(ws.name, ws.resource_group, ws.location, ws.subscription_id, sep = '\n')
   ```

2. Registre o modelo com o Azure Machine Learning.

   ```python
   from azureml.core.model import Model

   model = Model.register(model_path = "model.onnx",
                          model_name = "MyONNXmodel",
                          tags = ["onnx"],
                          description = "test",
                          workspace = ws)
   ```

3. Crie uma imagem com o modelo e todas as dependências.

   ```python
   from azureml.core.image import ContainerImage
   
   image_config = ContainerImage.image_configuration(execution_script = "score.py",
                                                     runtime = "python",
                                                     conda_file = "myenv.yml",
                                                     description = "test",
                                                     tags = ["onnx"]
                                                    )

   image = ContainerImage.create(name = "myonnxmodelimage",
                                 # this is the model object
                                 models = [model],
                                 image_config = image_config,
                                 workspace = ws)

   image.wait_for_creation(show_output = True)
   ```

   O arquivo `score.py` contém a lógica de pontuação e deve ser incluído na imagem. Esse arquivo é usado para executar o modelo na imagem. Confira este [tutorial](tutorial-deploy-models-with-aml.md#create-scoring-script) para obter instruções sobre como criar um script de pontuação. Um exemplo de arquivo para um modelo do ONNX é mostrado abaixo:

   ```python
   import onnxruntime
   import json
   import numpy as np
   import sys
   from azureml.core.model import Model

   def init():
       global model_path
       model_path = Model.get_model_path(model_name = 'MyONNXmodel')

   def run(raw_data):
       try:
           data = json.loads(raw_data)['data']
           data = np.array(data)
        
           sess = onnxruntime.InferenceSession(model_path)
           result = sess.run(["outY"], {"inX": data})
        
           return json.dumps({"result": result.tolist()})
       except Exception as e:
           result = str(e)
           return json.dumps({"error": result})
   ```

   O arquivo `myenv.yml` descreve as dependências necessárias para a imagem. Confira este [tutorial](tutorial-deploy-models-with-aml.md#create-environment-file) para obter instruções sobre como criar um arquivo de ambiente, como este arquivo de exemplo:

   ```python
   from azureml.core.conda_dependencies import CondaDependencies 

   myenv = CondaDependencies()
   myenv.add_pip_package("numpy")
   myenv.add_pip_package("azureml-core")
   myenv.add_pip_package("onnxruntime")

   with open("myenv.yml","w") as f:
    f.write(myenv.serialize_to_string())
   ```

4. Para implantar o modelo, consulte o documento[Como implantar e onde](how-to-deploy-and-where.md).


## <a name="examples"></a>Exemplos
 
Consulte [how-to-use-azureml/deployment/onnx](https://github.com/Azure/MachineLearningNotebooks/blob/master/how-to-use-azureml/deployment/onnx), por exemplo, notebooks que criam e implantam modelos ONNX.
 
[!INCLUDE [aml-clone-in-azure-notebook](../../../includes/aml-clone-for-examples.md)]

## <a name="more-info"></a>Mais informações

Saiba mais sobre ONNX ou colabore com o projeto:
+ [Site do projeto ONNX](https://onnx.ai)

+ [Código do ONNX no GitHub](https://github.com/onnx/onnx)

Saiba mais sobre o ONNX Runtime ou contribua para o projeto:
+ [Repositório GitHub do ONNX Runtime](https://github.com/Microsoft/onnxruntime)


