# -*- mode: Python -*
local_resource(
    'deploy',
    'python now.py > start-time.txt',
)

local_resource(
    'ingress',
    'kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/kind/deploy.yaml'
)

local_resource(
    'namespace',
    'kubectl apply -f namespace.yaml'
)
yaml = helm(
  'chart',
  name='my-very-first',
  namespace='my-very-first',
  values=['values-dev.yaml'],
)
k8s_yaml(yaml)
k8s_resource('my-very-first', resource_deps=['namespace'])


congrats = "🎉 Congrats, you ran a live_update! 🎉"
docker_build('example-python-image', '.', build_args={'flask_env': 'development'},
    live_update=[
        sync('.', '/app'),
        run('cd /app && pip install -r requirements.txt',
            trigger='./requirements.txt'),

        run('touch /app/app.py', trigger='./start-time.txt'),

        run('sed -i "s/Hello cats!/{}/g" /app/templates/index.html'.
            format(congrats)),
], ignore=[".git", "README.md"])