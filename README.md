## Test Tensorflow Serving

### train model

```
python mnist_saved_model.py --training_iteration=100 --model_version=1 /tmp
```

### deploy model

```
bazel build //tensorflow_serving/model_servers:tensorflow_model_server
bazel-bin/tensorflow_serving/model_servers/tensorflow_model_server --port=9000 --model_base_path=/tmp --model_name='mnist'
```

### gRPC request

```
python mnist_client.py --num_tests=10 --server='0.0.0.0:9000'
```