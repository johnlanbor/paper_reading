## Detection

### mixup precision

| gpus | fp 16 mode | training speed(iter/s) |             memory             |     batch size (single gpu)     |
| :--: | :--------: | :--------------------: | :----------------------------: | :-----------------------------: |
|  1   |     01     |          2.8           |             10267              | 8(fp16 loss) sometimes can work |
|  1   |    fp32    |          3.7           |              7183              |                4                |
|  1   |     01     |          4.5           |              8357              |                4                |
|  1   |     02     |          4.5           |              6965              |                4                |
|  2   |     01     |          3.5           |           9669/7813            |                4                |
|  2   |    fp32    |          3.65          |           8551/8481            |                4                |
|  4   |     01     |          3.2           |      8461/9101/6955/9443       |                4                |
|  4   |     01     |          2.8           | 8275/7995/8427/8565(half loss) |                4                |
|  4   |    fp32    |          3.1           |      8721/8861/9877/9413       |                4                |

#### note:

- [x] split loss from loss
- [x] use torch.nn.parrel.DistributedDataParallel to replace DataParral
- [ ] use apex to choose loss dtype