# pull official base image
FROM node:12.17.0-alpine

# set working directory
WORKDIR /app



# install app dependencies
COPY package.json ./

COPY yarn.lock ./
# create a .cache folder and give it read and write permission
# RUN yarn config set cache-folder ./  && yarn install --network-timeout=600000
RUN curl --silent --location https://dl.yarnpkg.com/rpm/yarn.repo |  tee /etc/yum.repos.d/yarn.repo
RUN yum install yarn
# RUN yarn install --network-timeout=600000

# mkdir -p /.cache && chmod 666 -R /.cache

# # attempt to remove access permissions 
# RUN chmod 777 -R ./

# # The default time out is far to short for openshift to install dependancies properly
# RUN yarn install --network-timeout=600000


# add app
COPY . ./

# start app
CMD ["yarn","start"]  